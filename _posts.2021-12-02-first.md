---
title: "Project Report: Independent Study of Automation and Robotics using UR Robot (ISE-837)"
author: "Yongseok Jeon, Kyoung Min Kim\n\nEdward P. Fitts Department of Industrial and Systems Engineering\n\nSupervisor: Dr. Yuanshin Lee, Dr. Ola Harryson, Dr. Jingyan Dong, Dr. Rohan Shirwaiker"
output:
  html_document:
    toc: true
    toc_depth: 2
---

# Timeline
- September
  - Learn how to perform the desired movement of UR robot by using controller
- October
  - Problem definition with automation process using UR robot and 6 blocks
- November
  - Building accessibility to UR robots through Intranet
  - Setting up environments for conveyor and the optical sensors
  - Establishing UR robot automation process system with stacking and classifying tasks

# Input environments
In this project, we conducted automation process (stacking and classifying) using UR robot and 6 blocks which have different color and size. Blocks are consist of 2x2 (red, yellow), 1x4 (green, skyblue, blue) and 1x3 (red). In addition, we have one conveyor belt with optical sensor and UR robot with task plate (see Figure 1). Moreover, iron brace is installed in the task plate, as will be illustrated, this iron brace was a key component that enabled us to perform stacking.

![6 blocks with one conveyor belt and UR robot](img/overall%20environments.png)

# Experiment

## Basic understanding of UR robot
To perform the desired movement of UR robot, we first need to understand the joint component of the robot. Figure 2 illustrates the overall joint position of UR5E. In detail, in order to move the robot into a specific position, we have to command 6 joint TCP (Tool Center Point) numeric variables (Base, Shoulder, Elbow, Wrist 1-3). Instead of manually putting 6 values, by using the controller (in manual mode), we were able to specify the certain movements.

![Joint position of UR5E robot](img/joint.png)

## Setting up environments for UR robot
In the first few weeks of practicing UR robot, we were able to perform certain movements using the gripper. However, since there was no camera installed in our robot, we had to manually install the camera using a hex wrench (shown in Fig 3). To activate the camera, we updated the related software and installed the USB driver. After setting up the camera, we found that the built-in function for identifying objects (with calibration) was not working. So far, as we were focusing on utilizing the controller, we had to turn our project direction from using the controller to implementing computer codes. That is, though the built-in function of UR robot was not working, since the camera itself was still working, we could substitute the built-in function using computer vision analysis (CV2 in Python).

To establish the connection between UR robot, we first need to connect to the intranet server (Wi-Fi). After connecting to the intranet, we get the accessibility for connected robots with certain IP addresses. Then using the `request` function in Python, we are able to get streaming images from the camera. Note that we need to set UR robot into remote control mode to make a connection. Moreover, to interact with the TCP position from the robot, we need to install the `ur_rtde` library from Python. To utilize the gripper, we need to compile a manual function named `RobotiqGripper` that was provided by the manufacturer.

![Gripper and camera installation in UR5E](img/gripper%20and%20camera.jpg)

## Setting up environments for Conveyor
In order to automate the process, we also need to control the conveyor belt through our code logic. Since the regarding library is not published online, similar to `RobotiqGripper` function in the previous section, we have to manually call the `MachineMotion.py` file as a library environment. In this project, we set our velocity and acceleration values as 50. Unlike UR robot, control information regarding conveyor are stored in a control box, thereby we have to set up another kernel for receiving optical sensor values (network id = 1, pin = 3). Those kernels return binary values whether the optical sensor detects the object or not. Hence, we can formulate the logic to stop the conveyor and reactivate it when needed.

## Image Analysis
To conduct the computer vision analysis for received images (from section 3.2), we installed `cv2` library, which is one of the well-known image analysis packages. Before we utilized the optical sensor from the conveyor, we tried to use camera information to detect the object to control the conveyor. However, since computing image analysis requires more time and has uncertainty than we expected, each time we get different stopping positions for the objects, thereby we modified this process by adapting the optical sensor in the conveyor. To classify the object in our interesting area on the conveyor (X: 200-350, Y: 150-500), we carried out multiple tests to obtain the representative (non-overlapping) HSV (Hue Saturation Value) values for each color (see Table 1). Once we classify the color of the object, we further apply the condition for identifying the shape of the block by calculating the length and height of the contour. For example, if we classify the object into the color of red, we calculate the width value from the contour and reclassify it into 2x2 or 1x3.

Nevertheless, there was still uncertainty in identifying objects. Occasionally, image analysis fails to capture the object at once, thereby keeps affecting the later operations. To mitigate this effect, we employed majority voting for decision making. In detail, we collect the image output for a certain amount of time, then make the final decision following majority rules. Throughout this process, we were able to obtain robust output (identifying blocks).

|            | Lower Bound (HSV) | Upper Bound (HSV) | Lower Bound (Area) | Upper Bound (Area) |
|------------|-------------------|-------------------|--------------------|--------------------|
| Red        | (150, 50, 70)    | (200, 255, 255)   | 5000               | 20000              |
| Green      | (40, 150, 50)    | (70, 255, 100)    | 5000               | 20000              |
| Blue       | (100, 200, 50)   | (130, 255, 255)   | 3000               | 20000              |
| Yellow     | (0, 100, 100)    | (50, 255, 255)    | 5000               | 20000              |

## Main algorithm
Our automation process can be grouped into two main tasks, stacking and classifying. Figure 4 illustrates the overall algorithmic procedures of our project. Before we start the automation process, we place the block in the middle of the conveyor in random order and then launch the process. First, we activate the conveyor to translocate the blocks into the sensor position. When the object approaches the optical sensor, we stop the conveyor and move the robot into the camera position. Then, following the majority rules addressed in the previous section (section 3.4), we identify the object and conduct the movement depending on the types of the block.

Here, we distinguished the process of the stacking depending on their order. Since our gripper cannot guarantee the stable position on the task plates, using the metal brace attached in the plate, we push the block from two different directions to ensure a constant position. Those processes are demonstrated in the attached video (0:43-0:52). Later, if we detect the second stacking block (2x2), we drop the secondary block into our ensured position and perform one-push to make an elaborate stacking output (see video 01:54-02:08). Other than 2x2 blocks will be classified and then placed into different positions depending on their colors. Finally, when the desired number of input was performed, we terminate the overall process.

![Algorithmic procedure for automation experiment](img/Overall-process.png)

# Notable Technical Issues

## Consistent network issue
While conducting our experiment, we observed multiple failures regarding connection problems (kernel dies in console output). Throughout the multiple experiments, we figured out that this problem was occurred due to the low frequency of network. That is, since we were mainly using 2.4 GHz network, if the movement command was conducted while exchanging information was not completed, it is likely corrupt the overall system. By switching the network from 2.4GHz into 5GHz, we resolved these issues.

## Initialization issue
In this section, we would like to discuss two different types of initialization problems, UR robot and conveyor. Similar to the previous section, when a certain problem occurs in the system and we retried the command, since the moving variable in the robot is still in progress, we face the system corruption. To avoid this issue, we found two strategies. The first approach is that we manually use the controller and change the mode of the system from remote control to manual control mode. By switching the mode of the UR robot, they initialize the overall process in progress, thereby we can start over. The secondary approach would be to manually insert the code `rtde_c.disconnect()` and `rtde_c.reconnect()`. We can avoid those issues by reconnecting method but this approach has drawbacks that sometimes due to some of the errors in interconnection in robot tends to make it hard to disconnect. Thereby, we would like to recommend manually change the mode of the system and restart the overall command.

# Conclusion

In this project, we learned how to construct the automation system and implement those processes. In fact, there were many more obstacles and issues that make it hard to overcome. Some of those problems were solved within a few weeks, but sometimes it took over 2 months to actually identify the real problem. We stated those long-lasting issues in section 4. Based on what we have learned in ISE-716 (Automated Systems Engineering), the most priority we concerned in this project is to reduce mistakes. In this respect, throughout this semester, we learned not only the needs of logical construction for automation but also the needs of constant feedback process to maintain sustainability.

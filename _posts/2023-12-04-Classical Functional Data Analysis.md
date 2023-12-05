---
title: "Classical Functional Data Analysis"
use_math: true
output:
  html_document:
    toc: true
    toc_depth: 2
---

# Timeline






# Input environments
In this project, we conducted automation process (stacking and classifying) using UR robot and 6 blocks which have different color and size. Blocks are consist of 2x2 (red, yellow), 1x4 (green, skyblue, blue) and 1x3 (red). In addition, we have one conveyor belt with optical sensor and UR robot with task plate (see Figure 1). Moreover, iron brace is installed in the task plate, as will be illustrated, this iron brace was a key component that enabled us to perform stacking.

![6 blocks with one conveyor belt and UR robot](/images/Untitled.jpeg)

# Experiment

## Basic understanding of UR robot
To perform the desired movement of UR robot, we first need to understand the joint component of the robot. Figure 2 illustrates the overall joint position of UR5E. In detail, in order to move the robot into a specific position, we have to command 6 joint TCP (Tool Center Point) numeric variables (Base, Shoulder, Elbow, Wrist 1-3). Instead of manually putting 6 values, by using the controller (in manual mode), we were able to specify the certain movements.














































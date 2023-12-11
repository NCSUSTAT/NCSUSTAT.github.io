---
use_math: true
classes: wide
---
<script type="text/javascript" async
  src="https://cdnjs.cloudflare.com/ajax/libs/mathjax/3.2.0/es5/tex-mml-chtml.js">
</script>



## Generation of Data 

We generated $X(t)$ from a Gaussian process. 

For the experiment, covariance functions were considered:

$C(s, t) = \sigma_{X(s)}\sigma_{X(t)}\rho(s, t)$ with the variance function $\sigma^2_X(t) = \sqrt{t}e^{-(t-0.1)^2/10+1}$ and the Matérn correlation function $\rho = (0.5, 1)$,


## Setting of Suggested New Estimator 

We use matern correlation function for model. 

- SNPTM(matern correlation function)

$\rho_{\theta}(s, t) = \frac{1}{\gamma{(\theta_1)} 2^{\theta_1-1}}(\sqrt{2\theta_1}\frac{|s-t|}{\theta_2})^{\theta_1}  B_{\theta_1}(\sqrt{2\theta_1}\frac{|s-t|}{\theta_2}), \theta_1, \theta_2>0$,
with  $B_{\theta}(.)$ being the modified Bessel function of the second kind of order $\theta$.


## Estimaors to compare 
- I.SNPTM
- II.PFBE (penalized Fourier basis expansion)
- III.PACE (Principal Analysis by Conditional Expectation)

## Comparison of Estimated Covariance function to the model generating Covariance function  

To evaluate the numerical performance of the proposed estimators, we generated $X(t)$ from a Gaussian process. with $\mu(t)=2s^{2} \sin(2\pi s)$, and Matérn correlation function $\rho = (0.5, 1)$ were considered:

Sample sizes $n = 200$ were considered to illustrate the behavior of the estimators. We set the domain $T = [0, 1]$. 

We compare estimated covariance functions of three estimators to the model generating Covariance function 
with different combination of settings: $\delta = 0.3, 0.5, 0.8$ and $m=5, 15$,

where $\delta$ is length of functional fragment and $m$ is sampling rate.

## Result
- setting
   -Figure1:  $m = 5$, $\delta =0.3$
  
   -Figure2:  $m = 5$, $\delta =0.5$

   -Figure3:  $m = 5$, $\delta =0.8$

   -Figure4:  $m = 15$, $\delta =0.3$

   -Figure5:  $m = 15$, $\delta =0.5$

   -Figure6:  $m = 15$, $\delta =0.8$



                      
                         
                         Figure1
                         
<div style="text-align:center;">
   <img src="/images/p1.png" alt="Figure 1: The design of covariance function from spinal bone mineral density data" width="50%">
</div>


                        Figure2: $m = 5$, $\delta =0.3$
                         
<div style="text-align:center;">
   <img src="/images/p2.png" alt="Figure 1: The design of covariance function from spinal bone mineral density data" width="50%">
</div>


                        Figure3: $m = 5$, $\delta =0.8$
                         
<div style="text-align:center;">
   <img src="/images/p3.png" alt="Figure 1: The design of covariance function from spinal bone mineral density data" width="50%">
</div>



                       Figure4: $m = 15$, $\delta =0.3$
                         
<div style="text-align:center;">
   <img src="/images/p4.png" alt="Figure 1: The design of covariance function from spinal bone mineral density data" width="50%">
</div>



                      Figure5: $m = 15$, $\delta =0.5$
                          
<div style="text-align:center;">
   <img src="/images/p5.png" alt="Figure 1: The design of covariance function from spinal bone mineral density data" width="50%">
</div>


                      Figure6: $m = 15$, $\delta =0.8$
                          
<div style="text-align:center;">
   <img src="/images/p5.png" alt="Figure 1: The design of covariance function from spinal bone mineral density data" width="50%">
</div>




## Result Analysis 



























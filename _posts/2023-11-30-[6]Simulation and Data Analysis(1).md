---
use_math: true
classes: wide
---
<script type="text/javascript" async
  src="https://cdnjs.cloudflare.com/ajax/libs/mathjax/3.2.0/es5/tex-mml-chtml.js">
</script>



## Setting of Suggested New Estimator 
In the suggested novel model(SNPT) in [5], the covariance function can be decomposed into two parts, a variance function and a correlation structure, i.e., $C(s, t) = \sigma^2_X(s) \sigma^2_X(t) \rho(s, t)$, where $\sigma^2_X(t)$ is the variance function of $X$, or more precisely, $\sigma^2_X(t) = E[(X(t) - \mu(t))^2]$, and $\rho(s, t)$ is the correlation function.

We can use matern correlation function for $\rho(s, t)$. 

- SNPTM(matern correlation function)

$\rho_{\theta}(s, t) = \frac{1}{\gamma{(\theta_1)} 2^{\theta_1-1}}(\sqrt{2\theta_1}\frac{\|s-t\|}{\theta_2})^{\theta_1} B_{\theta_1}(\sqrt{2\theta_1}\frac{\|s-t\|}{\theta_2}), \theta_1, \theta_2>0$, with  $B_{\theta}(.)$ being the modified Bessel function of the second kind of order $\theta$.


## Estimaors to compare 
- I.SNPTM
- II.PFBE (penalized Fourier basis expansion)
- III.PACE (Principal Analysis by Conditional Expectation)

## Comparison of Estimated Covariance function to the model generating Covariance function  

To evaluate the performance of the proposed estimators, we generated $X(t)$ from a Gaussian process with $\mu(t)=2t^{2} \sin(2\pi t)$, and $C(s, t) = \sigma_{X(s)}\sigma_{X(t)}\rho(s, t)$, where the variance function $\sigma^2_X(t) = 1$, Matérn correlation function with $\theta= (1, 1)$:

Sample sizes $n = 200$ were considered to illustrate the behavior of the estimators, and we set domain $T = [0, 1]$. 

We compare estimated covariance functions of three estimators to the model generating Covariance function 
with different combination of settings: $\delta = 0.3, 0.5, 0.8$ and $m=5, 15$,

where $\delta$ is defined as below:

   - Functional data with the following property: each function $X_i$ is only observed on a subject-specific interval $O_i = [A_i, B_i] \subseteq [a, b]$

   - There exists an absolute constant $\delta$ such that $0 < \delta < 1$ and  $B_i - A_i \leq \delta(b - a)$ for all $i = 1, 2, \ldots$

and $m$ represents the average number of measurements per curve. 

## Result
- Setting
  
   - Figure1:  $m = 5$, $\delta =0.3$
  
   - Figure2:  $m = 5$, $\delta =0.5$

   - Figure3:  $m = 5$, $\delta =0.8$

   - Figure4:  $m = 15$, $\delta =0.3$

   - Figure5:  $m = 15$, $\delta =0.5$

   - Figure6:  $m = 15$, $\delta =0.8$


                      
                         
                                                 
                         
<div style="text-align:center;">
    <p>Figure1: \( m = 5 \), \( \delta = 0.3 \) </p>
   <img src="/images/p1.png" alt="Figure 1: The design of covariance function from spinal bone mineral density data" width="80%">
</div>




                                               
                         
<div style="text-align:center;">
    <p>Figure2: \( m = 5 \), \( \delta = 0.5 \) </p>
   <img src="/images/p2.png" alt="Figure 1: The design of covariance function from spinal bone mineral density data" width="80%">
</div>





                         
<div style="text-align:center;">
    <p>Figure3: \( m = 5 \), \( \delta = 0.8 \) </p>
   <img src="/images/p3.png" alt="Figure 1: The design of covariance function from spinal bone mineral density data" width="80%">
</div>




                                            


                         
<div style="text-align:center;">
    <p>Figure4: \( m = 15 \), \( \delta = 0.3 \) </p>
   <img src="/images/p4.png" alt="Figure 1: The design of covariance function from spinal bone mineral density data" width="80%">
</div>






                          
<div style="text-align:center;">
    <p>Figure5: \( m = 15 \), \( \delta = 0.5 \) </p>
   <img src="/images/p5.png" alt="Figure 1: The design of covariance function from spinal bone mineral density data" width="80%">
</div>







                                             
                          
<div style="text-align:center;">
    <p>Figure6: \( m = 15 \), \( \delta = 0.8 \) </p>
   <img src="/images/p5.png" alt="Figure 1: The design of covariance function from spinal bone mineral density data" width="80%">
</div>




## Result Analysis 

- For clarity, in each figure that illustrates the covariance function estimation using PACE, we have designated infinity as the maximum real value of the entire estimated covariance function.

- In every figure, the (2,2) element represents the covariance function $C(s, t) = \sigma_{X(s)}\sigma_{X(t)}\rho(s, t)$ of the distribution that generates the data. This function incorporates the variance function $\sigma^2_X(t) = 1$ , and Matérn correlation function  with $\theta= (1, 1)$. Consequently, SNPTM demonstrates superior performance since the model is accurately specified for SNPTM in this context. For each sampling rate, as $\delta$ increases, we observe a corresponding increase in the smoothness of the estimated covariance function. Even in non-sparse functional snippets data($\delta$=0.3), the non-smoothness of the estimated covariance functions in SNPTM is still apparent. This can be easily deduced because the variance function is estimated through kernel smoothing, and the correlation parameter is obtained from an optimization that involves the estimated variance function. These observations suggest that SNPTM may still be susceptible to the limitations posed by the data with functional snippets.
  
- As we highlighted in [5]New Estimator for Analyzing Functional Snippets (SNPT), the PACE estimate suffers from significant boundary effects due to missing data in the off-diagonal region and insufficient observations at the two ends of the diagonal region. Additionally, boundary effects are evident even in scenarios close to "non-snippet and non-sparse functional data", where $\delta$=0.8, $n$=200, and $m$=15. Therefore, caution is advised when applying PACE to data that exhibit even a slight quality of functional snippets.

- PFBE demonstrates effective performance in estimating patterns where the Matérn correlation function rapidly decays to zero as design points diverge from the diagonal. However, in sparse settings (with m=5), it shows poor performance in the estimation of the variance function. In dense settings (with m=15), this issue appears to be mitigated.

- In this experiment, SNPTM outperforms other since in this case the model is corretly specified for SNPTM. To select a method in practice, one can first produce a scatter plot of the raw covariance function. If the function appears to decay monotonically as the point (s, t) moves away from the diagonal, then SNPT with a monotonic decaying correlation such as SNPTM is recommended. Otherwise, SNPT with a general correlation structure such as SNPTF or the PFBE approach might be adopted. 

## REFERENCE
[1] Li, J., Wang, Q., & Zhang, S. (2021). Mean and Covariance Estimation for Functional Snippets. Journal of the American Statistical Association, 25(3), 123-145.

























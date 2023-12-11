---
use_math: true
classes: wide
---


## Generation of Data 

We generated $X(t)$ from a Gaussian process. For the experiment, covariance functions were considered:

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

## Estimated Covariance function  

To evaluate the numerical performance of the proposed estimators, we generated $X(t)$ from a Gaussian process. with $\mu(t)=2s^{2} \sin(2\pi s)$, and Matérn correlation function $\rho = (0.5, 1)$ were considered:

sample sizes $n = 200$ were considered to illustrate the behavior of the estimators. We set the domain $T = [0, 1]$. 


and $\delta = 0.5$.

![Estimated Covariance Function(PACE)](/images/PACE_1.png)

![Estimated Covariance Function(PFBE)](/images/PFBE.png)

![Estimated Covariance Function(SNPTM)](/images/SNPTM.png)


























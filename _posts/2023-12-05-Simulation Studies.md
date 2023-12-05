---
use_math: true
---

## Generation of Data 
 
We generated $X(t)$ from a Gaussian process. Three different covariance functions were considered:

I. $C(s, t) = \sigma_{X(s)}\sigma_{X(t)}\rho(s, t)$ with the variance function $\sigma^2_X(t) = \sqrt{t}e^{-(t-0.1)^2/10+1}$ and the Matérn correlation function $\rho = (0.5, 1)$,

II. $C(s, t) = \Sigma_{k=1}^{50} 2k^{-\nu}\phi_k(s)\phi_k(t)$ with $\nu = 2$ and Fourier basis functions $\phi_k(t) = \sqrt{2}\sin(2k\pi t)$,

III. $C(s, t) = \Sigma_{1 \leq j, k \leq 5} c_{jk}\phi_j(s)\phi_k(t)$ with $c_{jk} =  
\frac{e^{|j - k|}}{5}$.



## Setting of Suggested New Estimator 



## Estimaors to compare 




## Estimated Covariance function  



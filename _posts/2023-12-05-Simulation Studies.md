---
use_math: true
---

## Generation of Data 
 
We generated $X(t)$ from a Gaussian process. Three different covariance functions were considered:

I. $C(s, t) = \sigma_{X(s)}\sigma_{X(t)}\rho(s, t)$ with the variance function $\sigma^2_X(t) = \sqrt{t}e^{-(t-0.1)^2/10+1}$ and the Matérn correlation function $\rho = (0.5, 1)$,

II. $C(s, t) = \Sigma_{k=1}^{50} 2k^{-\nu}\phi_k(s)\phi_k(t)$ with $\nu = 2$ and Fourier basis functions $\phi_k(t) = \sqrt{2}\sin(2k\pi t)$,

III. $C(s, t) = \Sigma_{1 \leq j, k \leq 5} c_{jk}\phi_j(s)\phi_k(t)$ with $c_{jk} = \frac{e^{|j - k|}}{5}$.



## Setting of Suggested New Estimator 

We use two types of correlation function for model. 
I.SNPTM(matern correlation function)
$\rho(s, t) = \frac{1}{(2\pi\theta_1^2)^{\frac{1}{2}}} \exp\left(-\frac{1}{2\theta_1^2}(s - t)^2\right) \left(\frac{1}{\theta_2}\right)^{\theta_1} \left|s - t\right|^{\theta_1 - 1} B_{\theta_1}\left(\frac{|s - t|}{\theta_2}\right)$

where $B_{\theta_1}(\cdot)$ is the modified Bessel function of the second kind of order $\theta_1$, and $\theta_1$ and $\theta_2$ are positive constants.

II.SNPTF
The correlation function $\rho$ falls into $\mathcal{F}_n$, a $d_n$-dimensional family of models for correlation functions, when the sample size is $n$.
Here, the dimension typically grows with the sample size. For example, one might consider a $d_n$-Fourier basis family:

$\rho(s, t) = \frac{1}{\sqrt{\phi(s)\phi(t)}} \sum_{j=1}^{d_n} \theta_j\varphi_j(s)\varphi_j(t), \quad \text{where} \quad 0 \leq \theta_1, \ldots, \theta_{d_n} \leq 0$

and

$\Sigma_{j=1}^{d_n} \theta_j = 1$,
where $\phi(t) = \left(\Sigma_{j=1}^{d_n} (\varphi_j)^2(t)\right)^{\frac{1}{2}}$ and $\{\varphi_1, \ldots\}$ are fixed orthonormal Fourier basis functions defined on $T$.

## Estimaors to compare 




## Estimated Covariance function  



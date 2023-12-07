---
use_math: true

---



## Generation of Data 
 
We generated $X(t)$ from a Gaussian process. Three different covariance functions were considered:

I. $C(s, t) = \sigma_{X(s)}\sigma_{X(t)}\rho(s, t)$ with the variance function $\sigma^2_X(t) = \sqrt{t}e^{-(t-0.1)^2/10+1}$ and the Matérn correlation function $\rho = (0.5, 1)$,

II. $C(s, t) = \Sigma_{k=1}^{50} 2k^{-\nu}\phi_k(s)\phi_k(t)$ with $\nu = 2$ and Fourier basis functions $\phi_k(t) = \sqrt{2}\sin(2k\pi t)$,

III. $C(s, t) = \Sigma_{1 \leq j, k \leq 5} c_{jk}\phi_j(s)\phi_k(t)$ with $c_{jk} = \frac{e^{\|j - k\|}}{5}$.



## Setting of Suggested New Estimator 

We use two types of correlation function for model. 

I.SNPTM(matern correlation function)

$\rho_{\theta}(s, t) = \frac{1}{\gamma{(\theta_1)} 2^{\theta_1-1}}(\sqrt{2\theta_1}\frac{|s-t|}{\theta_2})^{\theta_1}  B_{\theta_1}(\sqrt{2\theta_1}\frac{|s-t|}{\theta_2}), \theta_1, \theta_2>0$,
with  $B_{\theta}(.)$ being the modified Bessel function of the second kind of order $\theta$.


II.SNPTF

The correlation function $\rho$ falls into $\mathcal{F}_n$, a $d_n$-dimensional family of models for correlation functions, when the sample size is $n$.
Here, the dimension typically grows with the sample size. For example, one might consider a $d_n$-Fourier basis family:

$\rho(s, t) = \frac{1}{\sqrt{\phi(s)\phi(t)}} \Sigma_{j=1}^{d_n} \theta_j\varphi_j(s)\varphi_j(t), \quad \text{where} \quad 0 \leq \theta_1, \ldots, \theta_{d_n} \leq 0$

and

$\Sigma_{j=1}^{d_n} \theta_j = 1$,
where $\phi(t) = \left(\Sigma_{j=1}^{d_n} (\varphi_j)^2(t)\right)^{\frac{1}{2}}$ and $\{\varphi_1, \ldots\}$ are fixed orthonormal Fourier basis functions defined on $T$.

## Estimaors to compare 
- I.SNPTM
- II.SNPTF
- III.PFBE (penalized Fourier basis expansion)
- VI. PACE (Principal Analysis by Conditional Expectation)

## Estimated Covariance function  



To evaluate the numerical performance of the proposed estimators, we generated $X(t)$ from a Gaussian process. Matérn correlation function $\rho = (0.5, 1)$ were considered:

sample sizes $n = 100$ were considered to illustrate the behavior of the estimators. We set the domain $T = [0, 1]$ and $\delta = 0.5$.

![Estimated Covariance Function(PACE)](/images/PACE_1.png)

![Estimated Covariance Function(PFBE)](/images/PFBE.png)

![Estimated Covariance Function(SNPTM)](/images/SNPTM.png)








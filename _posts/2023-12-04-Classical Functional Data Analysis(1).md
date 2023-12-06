---
use_math: true
---

classical functional data analysis requires a large number of regularly spaced measurements per subject, in contrast to the modern method wich can adapt to  the case of irregularly spaced, sparse longitudinal data, and  the number of repeated measurements available per subject is small. Additionally, the FPC scores are defined through the Karhunen–Loève expansion. 

However, when the time points vary widely across subjects and are sparse, down to one or two measurements, FPC scores defined through the Karhunen–Loève expansion are not well approximated by the usual integration method.

















## Signal Functional Form

$\{s_i(t)\}$: observed signals, $i=1, \ldots, N$

$\mu(t)$: continuous functional mean

$\epsilon_i(t)$: realizations from a stochastic process with mean function 0 and covariance function $C(t,t')$

It includes both random noise and signal-to-signal variations.

$\rightarrow s_i(t) = \mu(t) + \epsilon_i(t)$

## Karhunen–Loeve Theorem

Using the Karhunen–Loeve Theorem, $\epsilon(t)$ can be written as:


$\epsilon(t) = \Sigma_{i=1}^{\infty} \xi_{ik} \phi_k(t)$


Where $\xi_{ik}$ are zero-mean and uncorrelated coefficients, i.e., $\mathbb{E}(\xi_{ik}) = 0$ and $\mathbb{E}(\xi_{ik}^2) = \lambda_k$, and $\phi_k(t)$ are eigen-functions of the covariance 

function $C(t,t')$:


$C(t,t') = \Sigma_{k=1}^{\infty} \lambda_k \phi_k(t) \phi_k(t')$


where $\lambda_1 \geq \lambda_2 \geq \ldots$ are ordered eigenvalues. The eigenfunctions can be obtained by solving:


$\int_{0}^{M} C(t,t') \phi_k(t') dt' = \lambda_k \phi_k(t)$


## Functional PCA

The variance of $\xi_{ik}$ quickly decays with $k$. Therefore, only a few $\xi_{ik}$, also known as FPC-scores, would be enough to accurately approximate the noise function. That is, the signal 

decomposition is given by:


$\epsilon_i(t) \approx \Sigma_{k=1}^{K} \xi_{i,k} \phi_k(t)$


Where:

$s_i(t) = \mu(t) + \epsilon_i(t) \approx \mu(t) + \Sigma_{k=1}^{K} \xi_{i,k} \phi_k(t)$


Here, $\xi_{i,k}$ are the FPC-scores, and $\phi_k(t)$ are the eigenfunctions of the covariance function.


## Computing FPC-Scores

To compute the eigen-function $\hat{\phi}_k(t_j)$, we solve the integral equation:

$\int_{0}^{M} \hat{C}(t, t') \hat{\phi}_k(t)dt = \hat{\lambda}_k\hat{\phi}_k(t') $

$\int_{0}^{M} \hat{\phi}_k(t) \cdot \hat{\phi}_m(t) dt :=(1,   if  \ m = k), (0,   if  \ m \neq k) $

- $\int_0^M \phi_k(t) \cdot \phi_m(t) \, dt$ represents the integral of the product of eigenfunctions \\

 $\phi_k(t)$ and $\phi_m(t)$ over the interval [0, M]. The equation evaluates to 1 if $m$ equals $k$ (i.e., $m = k$), indicating that the eigenfunctions are orthonormal for the same index.\\

- The equation evaluates to 0 if $m$ is not equal to $k$ (i.e., $m \neq k$), indicating that the eigenfunctions are orthogonal for different indices.



-This is solved by discretizing the estimated covariance function $\hat{C}(t_j, t_j')$.

-To compute the FPC-scores $\hat{\zeta}_{ik}$, we use numerical integration, where $t_0 = 0$. The integration formula is as follows:


$\hat{\zeta}_{ik} = \Sigma_{j=1}^{J} (s_i(t_j) - \hat{\mu}(t_j)) \cdot \hat{\phi}_k(t_j) \cdot \Delta t_j$


Where:
- $\Delta t_j = t_j - t_{j-1}$ (assuming regular grid points)
- $\hat{\zeta}_{ik}$ are the FPC-scores for observation $i$.



## Reference









































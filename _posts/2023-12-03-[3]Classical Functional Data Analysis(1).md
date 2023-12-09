---
use_math: true
---
## Introduction
Classical functional data analysis requires a substantial number of regularly spaced measurements per subject. In contrast, modern methods are adaptable to scenarios involving irregularly spaced, sparse longitudinal data, even when there are few repeated measurements per subject.

Additionally, Functional Principal Component (FPC) scores are typically defined using the Karhunen–Loève expansion. However, in cases where the time points vary widely across subjects and are sparse, sometimes comprising only one or two measurements, the FPC scores defined through the Karhunen–Loève expansion may not be well approximated using the standard integration method.

In the following post, we will delve into the advancements of modern models that accommodate irregularly spaced, sparse longitudinal data.

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


$\epsilon_i(t)\approx\Sigma_{k=1}^{K}\xi_{i,k}\phi_k(t)$


Where:

$s_i(t)=\mu(t)+\epsilon_i(t)\approx\mu(t)+\Sigma_{k=1}^{K}\xi_{i,k}\phi_k(t)$


Here, $\xi_{i,k}$ are the FPC-scores, and $\phi_k(t)$ are the eigenfunctions of the covariance function.


## Computing FPC-Scores

To compute the eigen-function $\hat{\phi}_k(t_j)$, we solve the integral equation:

$\int_{0}^{M} \hat{C}(t, t')\hat{\phi}_k(t)dt=\hat{\lambda}_k\hat{\phi}_k(t')$

$\int_{0}^{M} \hat{\phi}_k(t)\hat{\phi}_m(t)dt :=(1, if \ m = k), (0, if \ m \neq k)$

The equation evaluates to 0 if $m$ is not equal to $k$ (i.e., $m \neq k$), indicating that the eigenfunctions are orthogonal for different indices.

This is solved by discretizing the estimated covariance function $\hat{C}(t_j, t_j')$.

To compute the FPC-scores $\hat{\xi}_{ik}$, we use numerical integration, where $t_0 = 0$. The integration formula is as follows:

- computing FPC-scores: 

$\hat{\xi_{ik}}=\int_{0}^{M}(s_i(t)-\hat{\mu}(t))\phi_k(t)dt$

$\hat{\xi_{ik}}\approx\Sigma_{j=1}^{J} (s_i(t_j)-\hat{\mu}(t_j))\hat{\phi_k}(t_j)(t_{j}-t_{j-1})$


## FPC-Scores

 In multivarate data analysis, when $X_{n,p}$, $E\[X\]=\mu$, and sample covariance matrix is $C=(X-\mu)^{T}(X-\mu)$, $j th$ Pricipal component score is expressed as $z_{j}=(X-\mu)H_j$, where $C=\Sigma_{i=1}^{p}\lambda_i H_i H_i^T$. Similarly, in FPCA, we assume that the infinite-dimensional processes under consideration are well approximated by the projection on the
function space spanned by the first M eigenfunctions, and $j th$ Functional Pricipal component score is expressed as $z_j=\int (X(t)-\mu(t))H_j(t)dt$=
$\langle X(t)-\mu(t),H_j(t) \rangle$, where $C(t,t')=\Sigma_j \lambda_j H_j(t) H_j(t')^Tdt$ by Karhunen–Loeve Theorem.


## REFERENCES
[1]Dr. Xiaolei Fang, (2023). ISE789 Lecture note

[2]Yao, F., Müller, H.-G., & Wang, J.-L. (2005). Functional Data Analysis for Sparse Longitudinal Data. Journal of the American Statistical Association























































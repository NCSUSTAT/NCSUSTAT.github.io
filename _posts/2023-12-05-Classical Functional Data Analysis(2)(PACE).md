
---

use_math: true

---



## Model Estimation
  Complete signals: sampled regularly
  
  Incomplete signals: sampled irregularly, sparse, fragmented
  
## Estimation of Mean Function

Historical signals $s_{ij}$:

  i=1,...,N: signal index
  
  j=1,...,m_i: observation index in each signal

 $S_{i}(t_{ij}) \approx \mu(t_{ij}) + \Sigma_{k=1}^{K} \xi_{ik} \varphi_{k}(t_{ij})$

We can estimate the mean function $\hat{\mu}(t)$ using local linear regression by minimizing:

 $\min_{c_0,c_1}\Sigma_{i=1}^{n} \Sigma_{j=1}^{m_i} W(\frac{t_i - t_{ij}}{h})(s_{i}(t_{ij}) - c_0 - (t - t_{ij})c_1 )^2$


The solution is given by:

$\hat{\mu}(t) = \hat{c}_0(t)$

## Estimation of Covariance Function

First, we use the estimated mean functions to estimate the raw covariance function $\hat{C}(t, t'):$

$\hat{C_i}(t_{ij}, t_{ik}) = (s_i(t_{ij}) - \hat{\mu}(t_{ij}))(s_i(t_{ik}) - \hat{\mu}(t_{ik}))$

- $\hat{C_i}(t_{ij}, t_{ik})$ is the covariance between observations $i$ at times $t_{ij}$ and $t_{ik}$.
- $s_i(t_{ij})$ is the signal at observation $i$ and time $t_{ij}$.
- $\hat{\mu}(t_{ij})$ is the estimated mean function at time $t_{ij}$.
- $s_i(t_{ik})$ is the signal at observation $i$ and time $t_{ik}$.
- $\hat{\mu}(t_{ik})$ is the estimated mean function at time $t_{ik}$.

The minimization problem is as follows:

$\min_{c_0, c_1, c_2} \Sigma_{i=1}^{n} \Sigma_{1 \leq j \neq k \leq m_i} W(\frac{t_{i,j} - t}{h},\frac{t_{i,k} - t}{h}) (\hat{C}(t_{i,j}, t_{i,k}) - c_0 - c_1(t - t_{i,j}) - c_2(t' - t_{i,k}))^2$

To estimate the covariance surface $\hat{C}(t, t')$, we use local quadratic regression. The solution is given by:

$\hat{C}(t, t') = \hat{c}_0(t, t')$

To solve the estimated covariance function, $\hat{\phi}_k(t)$ is estimated by discretizing the estimated covariance function $\hat{C}(t, t')$.

## Computing FPC-Scores

To compute the eigen-function $\hat{\phi}_k(t_j)$, we solve the integral equation:

$\int_{0}^{M} \hat{C}(t, t') \hat{\phi}_k(t)dt = \hat{\lambda}_k\hat{\phi}_k(t') $

$\int_{0}^{M} \hat{\phi}_k(t) \cdot \hat{\phi}_m(t) dt :=(1,   if  \ m = k), (0,   if  \ m \neq k) $

The equation evaluates to 0 if $m$ is not equal to $k$ (i.e., $m \neq k$), indicating that the eigenfunctions are orthogonal for different indices.

This is solved by discretizing the estimated covariance function $\hat{C}(t_j, t_j')$.

To compute the FPC-scores $\hat{\xi}_{ik}$, we use numerical integration, where $t_0 = 0$. The integration formula is as follows:

- computing FPC-scores: 

$\hat{\xi_{ik}}=\int_{0}^{M}(s_i(t)-\hat{\mu}(t))\phi_k(t)dt $

$\hat{\xi_{ik}} \approx \Sigma_{j=1}^{J} (s_i(t_j) - \hat{\mu}(t_j)) \cdot \hat{\phi_k}(t_j) \cdot (t_{j}-t{j-1})$



## Reference
[1]Yao, F., Müller, H.-G., & Wang, J.-L. (2005). Functional Data Analysis for Sparse Longitudinal Data. Journal of the American Statistical Association




























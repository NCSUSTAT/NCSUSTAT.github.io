

$\textbullet$ Signal Functional Form

$\{s_i(t)\}$: observed signals, $i=1, \ldots, N$

$\mu(t)$: continuous functional mean

$\epsilon_i(t)$: realizations from a stochastic process with mean function 0 and covariance function $C(t,t')$
It includes both random noise and signal-to-signal variations.

$\rightarrow s_i(t) = \mu(t) + \epsilon_i(t)$

$\textbullet$ Karhunen–Loeve Theorem

Using the Karhunen–Loeve Theorem, $\epsilon(t)$ can be written as:


$\epsilon(t) = \sum{i=1}^{\infty} \xi_{ik} \phi_k(t)$


Where $\xi_{ik}$ are zero-mean and uncorrelated coefficients, i.e., $\mathbb{E}(\xi_{ik}) = 0$ and $\mathbb{E}(\xi_{ik}^2) = \lambda_k$, and $\phi_k(t)$ are eigen-functions of the covariance function $C(t,t')$:


$C(t,t') = \sum_{k=1}^{\infty} \lambda_k \phi_k(t) \phi_k(t')$


where $\lambda_1 \geq \lambda_2 \geq \ldots$ are ordered eigenvalues. The eigenfunctions can be obtained by solving:


$\int_{0}^{M} C(t,t') \phi_k(t') dt' = \lambda_k \phi_k(t)$


$\textbullet$ Functional PCA

The variance of $\xi_{ik}$ quickly decays with $k$. Therefore, only a few $\xi_{ik}$, also known as FPC-scores, would be enough to accurately approximate the noise function. That is, the signal decomposition is given by:


$\epsilon_i(t) \approx \sum_{k=1}^{K} \xi_{i,k} \phi_k(t)$


Where:

s_i(t) &= \mu(t) + \epsilon_i(t) \\
&\approx \mu(t) + \sum_{k=1}^{K} \xi_{i,k} \phi_k(t)


Here, $\xi_{i,k}$ are the FPC-scores, and $\phi_k(t)$ are the eigenfunctions of the covariance function.

$\textbullet$ Model Estimation

    $\item$ Complete signals: sampled regularly
    $\item$ Incomplete signals: sampled irregularly, sparse, fragmented



$\textbullet$ Estimation of Mean Function

Historical signals $s_{ij}$:

    $\item$ $i=1,\ldots,N$: signal index
    $\item$ $j=1,\ldots,m_i$: observation index in each signal




 $S_{i}(t_{ij}) \approx \mu(t_{ij}) + \sum_{k=1}^{K} \xi_{ik} \varphi_{k}(t_{ij})$


We can estimate the mean function $\hat{\mu}(t)$ using local linear regression by minimizing:

$\text{minimize_{(c_0,c_1)} }\  \mathcal{L}(\mathbf{c}_0, \mathbf{c}_1) = \sum_{i=1}^{n} \sum_{j=1}^{m_i} W(\frac{t_i - t_{ij}}{h}) \left \{{s_{ij} - c_0 - (t - t_{ij})c_1\}^2$


The solution is given by:

$\hat{\mu}(t) = \hat{c}_0(t)$


$\textbullet$ Estimation of Covariance Function

First, we use the estimated mean functions to estimate the raw covariance function $\hat{C}(t, t'):$

$\hat{C}_i(t_{ij}, t_{ik}) = (s_i(t_{ij}) - \hat{\mu}(t_{ij})) \cdot (s_i(t_{ik}) - \hat{\mu}(t_{ik}))$



-$\hat{C}_i(t_{ij}, t_{ik})$ is the covariance between observations $i$ at times $t_{ij}$ and $t_{ik}$.\\
- $s_i(t_{ij})$ is the signal at observation $i$ and time $t_{ij}$.\\
- $\hat{\mu}(t_{ij})$ is the estimated mean function at time $t_{ij}$.\\
- $s_i(t_{ik})$ is the signal at observation $i$ and time $t_{ik}$.\\
- $\hat{\mu}(t_{ik})$ is the estimated mean function at time $t_{ik}$.



The minimization problem is as follows:


$\min_{c_0, c_1, c_2} \sum_{i=1}^{n} \sum_{1 \leq j \neq k \leq m_i} W(\frac{t_{i,j} - t}{h},\frac{t_{i,k} - t}{h}) \left\{\hat{C}(t_{i,j}, t_{i,k}) - c_0 - c_1(t - t_{i,j}) - c_2(t' - t_{i,k})\right\}^2$



To estimate the covariance surface $\hat{C}(t, t')$, we use local quadratic regression. The solution is given by:


$\hat{C}(t, t') = \hat{c}_0(t, t')$


To solve the estimated covariance function, $\hat{\phi}_k(t)$ is estimated by discretizing the estimated covariance function $\hat{C}(t, t')$.

$\textbullet$ Computing FPC-Scores

To compute the eigen-function $\hat{\phi}_k(t_j)$, we solve the integral equation:


$\int_{0}^{M} \hat{C}(t, t') \hat{\phi}_k(t) \, dt = \hat{\lambda_{k}}\hat{\phi}_k(t') $

$\int_{0}^{M} \phi_k(t) \cdot \phi_m(t) \, dt :=
    (1, &  if  \ m = k),   \\
    (0, &  if  \ m \neq k)  \\
$



- $\int_0^M \phi_k(t) \cdot \phi_m(t) \, dt$ represents the integral of the product of eigenfunctions \\
$\phi_k(t)$ and $\phi_m(t)$ over the interval [0, M]. The equation evaluates to 1 if $m$ equals $k$ (i.e., $m = k$), indicating that the eigenfunctions are orthonormal for the same index.\\

- The equation evaluates to 0 if $m$ is not equal to $k$ (i.e., $m \neq k$), indicating that the eigenfunctions are orthogonal for different indices.



-This is solved by discretizing the estimated covariance function $\hat{C}(t_j, t_j')$.

-To compute the FPC-scores $\hat{\zeta}_{ik}$, we use numerical integration, where $t_0 = 0$. The integration formula is as follows:


$\hat{\zeta}_{ik} = \sum_{j=1}^{J} (s_i(t_j) - \hat{\mu}(t_j)) \cdot \hat{\phi}_k(t_j) \cdot \Delta t_j$


Where:
- $\Delta t_j = t_j - t_{j-1}$ (assuming regular grid points)
- $\hat{\zeta}_{ik}$ are the FPC-scores for observation $i$.












































---
use_math: true
---



## Introduction to PACE(Principal Analysis by Conditional Expectation)
  Classical functional data analysis requires a large number of regularly spaced measurements per subject. In contrast, We propose a nonparametric method to perform functional principal components analysis for the case of sparse longitudinal data. The method aims at irregularly spaced longitudinal data, where the number of repeated measurements available per subject is small.
  
## Improvements over Previous Studies
- The inclusion of additional measurement errors represents a significant improvement.
- The method effectively manages sparse and irregular longitudinal data.
   - In particular, it efficiently reconstructs random trajectories by integrating information from both individual cases and the entire dataset during the construction of estimated mean 
    functions, covariance functions, and the prediction of FPC scores through a Bayesian approach. I will elaborate on this process, emphasizing how the method leverages information from the 
    entire dataset to estimate individual trajectories.



  
## Estimation of Mean Function

Historical signals $s_{ij}$:

  $i=1,...,N$: signal index
  
  $j=1,...,m_i$: observation index in each signal

 $S_{i}(t_{ij}) = \mu(t_{ij}) + \Sigma_{k=1}^{\infty} \xi_{ik} \varphi_{k}(t_{ij}) + \epsilon_{ij}$, where $E(\epsilon_{ij})=0, var(\epsilon_{ij})=\sigma^{2}$

We can estimate the mean function $\hat{\mu}(t)$ using local linear regression by minimizing:

 $\min_{c_0,c_1}\Sigma_{i=1}^{n} \Sigma_{j=1}^{m_i} W(\frac{t - t_{ij}}{h})(s_{i}(t_{ij}) - c_0 - (t - t_{ij})c_1 )^2$


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

$\min_{c_0, c_1, c_2} \Sigma_{i=1}^{n} \Sigma_{1 \leq j \neq k \leq m_i} W(\frac{t_{i,j} - t}{h},\frac{t_{i,k} - t}{h}) (\hat{C_i}(t_{i,j}, t_{i,k}) - c_0 - c_1(t - t_{i,j}) - c_2(t' - t_{i,k}))^2$

To estimate the covariance surface $\hat{C}(t, t')$, we use local quadratic regression. The solution is given by:

$\hat{C}(t, t') = \hat{c}_0(t, t')$

To solve the estimated covariance function, $\hat{\phi}_k(t)$ is estimated by discretizing the estimated covariance function $\hat{C}(t, t')$.


![fragmented(middle), sparse(right) data set](/images/cov1.png)



## Graphical Illustration of Estimation of Covariance Function

![fragmented(middle), sparse(right) data set](/images/st793.jpg)


## CD4 Count Data in perspective of integrating information from both individual cases and the entire dataset

- The dataset considered here is from the Multicenter AIDS Cohort Study, which includes repeated measurements of physical exams, laboratory results, and CD4 percentages
for 283 homosexual men who became HIV-positive between 1984 and 1991. All individuals were scheduled to have their measurements made at semiannual visits. However, because
many individuals missed scheduled visits and the HIV infections happened randomly during the study, the data are sparse, with unequal numbers of repeated measurements per subject
and different measurement times, $T_{ij}$, per individual. The number of observations per subject ranged from 1 to 14, with a median of 6.

- That the data from such a classical longitudinal study, with measurements intended to be spaced at regular 6-month intervals, are quite well suited for analysis by PACE is illustrated by
Figure 2.

- Although the data available per subject are sparse, the assembled pairs $(T_{ij},T_{ik})$ are sufficiently dense in the domain plane, and estimation of the covariance function is feasible for these data.

![fragmented(middle), sparse(right) data set](/images/cd4.png)

## Computing FPC-Scores

The best prediction of the FPC scores for the $i th$ subject, given the data from that individual, is the conditional expectation, which, under Gaussian assumptions is found to be 

$\tilde{\xi_{ik}} = E[\xi_{ik}|\tilde{Y_i}] = \lambda_k \phi_{ik}^T \Sigma_{Y_i}^{-1}(\tilde{Y_i} - \mu_i) $
, where $\Sigma_{Y_i} = \text{cov}(\tilde{Y_i},\tilde{Y_i}) = \text{cov}(\tilde{X_i},\tilde{X_i}) + \sigma^2I_{N_i}$ 

From the fact that $G(s,t)=cov(\tilde{X}(s),\tilde{X}(t))$, the $(j, l)$ entry of the $N_i \times N_i$ matrix $\Sigma_{Y_i}$ is ${(\Sigma_{Y_i})}_{j,l}$

$=G(T_{ij},T_{il})+\sigma^2 \delta_{jl} \ -(1)$ 
 
 with $\delta_{jl} = 1$ if $j = l$ and $0$ if $j \neq l$.

Estimates for the FPC scores $\xi_{ik}$ are obtained from (1), by substituting estimates of $\mu_i$, $\lambda_k$, and $\phi_{ik}$, $\Sigma_{Y_i}$ obtained from the entire data ensemble, leading to $\hat{\xi_{ik}} = \hat{E}[\xi_{ik}|\tilde{Y_i}]$ 
$= \hat{\lambda_k}\hat{\phi_{ik}}^T\hat{\Sigma_{Y_i}}^{-1}(\tilde{Y_i} - \hat{\mu_i})$

where the $(j,l)th$ element of $\hat{\Sigma_{Y_i}}$ is ${\hat{(\Sigma_{Y_i})}}_{j,l}$

$=\hat{G}(T_{ij},T_{il}) + \hat{\sigma}^2\delta_{jl}$. 

where, $\xi_{ik}$ and $\epsilon_{ij}$ are jointly Gaussian. In all of what follows, the results pertaining to expectations are always conditional on the observation times $T_{ij}$, $i = 1, . . . , n$, $j = 1, . . . , N_i$. For simplicity, the dependence on $T_{ij}$ is suppressed. Write $\tilde{X_i} = (X_i(T_{i1}), . . . , X_i(T_{iN_i}))^T, \tilde{Y_i} = (Y_{i1}, . . . , Y_{iN_i})^T,$
$\mu_i = (\mu(T_{i1}), . . . , \mu(T_{iN_i}))^T, and \  \phi_{ik} = (\phi_k(T_{i1}), . . . , \phi_k(T_{iN_i}))^T.$


## Bayesian Approach in perspective of integrating information from both individual cases and the entire dataset

- For the estimator of the FPC scores, $\hat{\xi}_{ik}$ =

  $ \hat{E}[\xi_{ik} | \tilde{Y}_i] = \hat{\lambda_k} \hat{\phi_{ik}} \hat{\Sigma_{Y_i}}^{-1} (\tilde{Y_i} - \hat{\mu_i})$, the quantities
$\lambda_k$ and $\Sigma_{Y_i}$ are estimated from the entire dataset, borrowing strength from the data on all subjects.




## Reference

[1]Dr. Xiaolei Fang, (2023). ISE789 Lecture note

[2]Yao, F., Müller, H.-G., & Wang, J.-L. (2005). Functional Data Analysis for Sparse Longitudinal Data. Journal of the American Statistical Association














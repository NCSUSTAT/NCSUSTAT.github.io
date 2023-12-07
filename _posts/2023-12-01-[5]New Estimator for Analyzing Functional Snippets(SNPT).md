---
use_math: true
---

## Introduction
- The studies are concerned with the estimation of the average and covariance functions for functional snippets, which are brief portions of functions that may be observed sporadically within a specific subinterval considerably shorter than the entire study period. Estimating the covariance function for these functional snippets presents a challenge because information about the distant, off-diagonal portions of the covariance structure is entirely absent.
  

## Definition of Functional Snippets Data 
 - The phenomenon that each individual trajectory is only recorded in an individual specic subinterval that is much shorter than the span of the study.
 - Mathematical Expression: 

   - Subjects enter the study at random times and are followed for a short period within the domain $T = [a, b] \subseteq R$. 

   - Specifically, we focus on functional data with the following property: each function $X_i$ is only observed on a subject-specific interval $O_i = [A_i, B_i] \subseteq [a, b]$

   - (S) There exists an absolute constant $\delta$ such that $0 < \delta < 1$ and  $B_i - A_i \leq \delta(b - a)$ for all $i = 1, 2, \ldots$

   - As a result, the design of support points (Yao et al., 2005) where one has information about the covariance function $C(s, t)$ is incomplete in the sense that there are no design points in 
     the off-diagonal region $T_c^\delta = \{(s, t) \in [a, b]^2 : |s - t| > \delta(b - a),\ s, t \in [a, b] \}$.

   - This is mathematically characterized by $\bigcup_i ([A_i, B_i]^2) \cap T_{\delta}^{c} = \emptyset - (1)$.

## Example of Functional Snippets Data
  - An example is the spinal bone mineral density data collected from 423 subjects ranging in age from 8.8 to 26.2 years (Bachrach et al., 1999). The design plot for the covariance
function, as shown in Figure 1, indicates that all of the design points fall within a narrow band around the diagonal area but the domain of interest [8.8, 26.2] is much larger than this
band.

<div style="text-align:center;">
  <img src="/images/age.png" alt="Figure 1: The design of covariance function from spinal bone mineral density data">
</div>
Figure1: The design of covariance function from spinal bone mineral density data


 - The cause of this phenomenon is that each individual trajectory is only recorded in an individual specific subinterval that is much shorter than the span of the study. For the spinal bone mineral density data, the span (length of interval between the first measurement and the last one) for each individual is no larger than 4.3 years, while the span for the study is about 17 years. Data with this characteristic, mathematically described by (S) or (1), are called functional snippets in this paper, analogous to the longitudinal snippets studied in Dawson and Muller (2018).

## Limitation of PACE in the Estimation of Covariance Functional Snippets Data
 - PACE (Yao et al., 2005) is a local smoothing method that, unlike interpolation methods, fails to produce a consistent estimate of the covariance function in the off-diagonal region, as the problem requires data extrapolation. We will demonstrate the vulnerability of PACE for covariance function estimation at the boundary of the domain, where the number of design points is limited, in the Simulation Studies and Data Analysis sections.

 - In the Data Analysis for spinal bone mineral density data collected from 423 subjects ranging in age from 8.8 to 26.2 years (Bachrach et al., 1999), Li, J., Wang, Q., & Zhang, S. (2021) presented the phenomenon and the estimated covariance estimation function is as below(Figure2):
   
<div style="text-align:center;">
   <img src="/images/SNPT.png" alt="Figure 1: The design of covariance function from spinal bone mineral density data" width="50%">
</div>
  Figure2: The estimated covariance estimation functionby PACE

## SNPT in the Estimation of Covariance Functional Snippets Data
 - To overcome this challenge, SNPT tackle it by breaking down the covariance function into two components: a variance function component and a correlation function component. The variance component can be effectively estimated through nonparametric methods, while the correlation component is modeled parametrically, potentially involving an increasing number of parameters, to account for the missing data in the distant off-diagonal regions. Both theoretical analysis and numerical simulations indicate that this hybrid approach is highly effective. Furthermore, they introduce a novel estimator for the variance of measurement errors and examine its asymptotic properties. This estimator is essential for estimating the variance function when dealing with noisy measurements.

  
## Estimation of Mean Function 
 
 - Smoothing approaches such as Yao et al. (2005) can be applied to estimate the mean function $\mu$. 
 
## Estimation of Covariance Function 
 - the covariance function can be decomposed into two parts, a variance function and a correlation structure, i.e., $C(s, t) = \sigma^2_X(s) \sigma^2_X(t) \rho(s, t)$, where $\sigma^2_X(t)$ is the variance function of $X$, or more precisely, $\sigma^2_X(t) = E[(X(t) - \mu(t))^2]$, and $\rho(s, t)$ is the correlation function.
   
 - Estimation of variance Function:

   $(\hat{b_0},\hat{b_1}) = \arg \min_{(b_0, b_1) \in R^2} \Sigma_{i=1}^{n} w_i\Sigma_{j=1}^{m_i} Kh_{\sigma}(T_{ij} - t) \left(f(Y_{ij}) - \hat{\mu}(T_{ij})\right)^2 - b_0 - b_1(T_{ij} - t))^2$

   Then $\hat{b_0}=\tilde{\zeta}^2(t)$. Our estimate of $\sigma^2_X(t)$ is $\hat{\sigma}^2_X(t) = \hat{\zeta}^2(t) - \hat{\sigma}^2_0$, where $\hat{\sigma}^2_0$ is a new estimate of $\sigma^2_0$, where $\hat{\zeta}^2(t)$ is the ridged version of $\tilde{\zeta}^2(t)$, $\tilde{\zeta}^2(t)$ is the non-ridged local linear estimate of $\zeta^2(t)$, and $\sigma^2(t) = \mathbb{E}\left[(Y(t) - \mu(t))^2\right] = \sigma^2_X(t) + \sigma^2_0$

 - Estimation of Covariance Function:
$\hat{Q}_n(\theta) =$

$\Sigma_{i=1}^{n} \frac{1}{m_i(m_i - 1)} \Sigma_{1 \leq j \neq l \leq m_i}\left(\hat{\sigma_X}(T_{ij})\hat{\sigma_X}(T_{il})\hat{\rho}(T_{ij}, T_{il}) - C_{ijl}\right)^2,$ where $C_{ijl} = \left(Y_{ij} - \hat{\mu}(T_{ij})\right)\left(Y_{il} - \hat{\mu}(T_{il})\right)$ is the raw covariance of subject $i$ at two different measurement times, $T_{ij}$ and $T_{il}$.

    

   

 
## REFERENCE
- [1] Li, J., Wang, Q., & Zhang, S. (2021). Mean and Covariance Estimation for Functional Snippets. Journal of Statistics, 25(3), 123-145.
























---
use_math: true
classes: wide
---

## Sparse(right), fragmented(middle), irregularly sampled data  



![fragmented(middle), sparse(right) data set](/images/sp_img.png)

## Statistical issues in Sparse, fragmented, irregularly sampled data 


The FPC(Functional principal component) scores $\xi_{ik} = \int (X_i(t) - \mu(t))\phi_k(t) dt$ have traditionally
been estimated by numerical integration, which works
well when the density of the grid of measurements for each
subject is sufficiently large. 


$\hat{\xi_{ik}} = \Sigma_{j=1}^{J} (s_i(t_j) - \hat{\mu}(t_j)) \hat{\phi_k}(t_j) \Delta  t_j$


Where:
- $\Delta t_j = t_j - t_{j-1}$ 
- $\hat{\xi}_{ik}$ are the FPC-scores for observation $i$.


Because in our model the $Y_{ij}$ are available only at discrete random times $T_{ij}$, reflecting the sparseness of the data, the integrals in the definition of the FPC scores $\xi_{ik}$ accordingly would be approximated by sums, substituting $Y_{ij}$ for $X_i(T_{ij})$ and estimates $\hat{\mu}(t_{ij})$
for $\mu(t_{ij})$ and $\hat{\phi_k}(t_{ij})$ for $\phi_k(t_{ij})$, leading to $\hat{\xi_{ik}^{S}} = \Sigma_{j=1}^{N_i}(Y_{ij} - \hat{\mu}(T_{ij})) \hat{\phi_k}(T_{ij})(T_{ij} - T_{i,j-1})$, setting $T_{i0} = 0$. For sparse functional data, $\hat{\xi_{ik}^{S}}$ will not provide reasonable approximations to $\xi_{ik}$, for example, when one has only two observations per subject. Moreover, when the measurements are contaminated with errors, the underlying random process $X$ cannot be directly observed. Substituting $Y_{ij}$ for $X_i(T_{ij})$ then leads to biased
FPC scores. These considerations motivate the alternative method to obtain the FPC scores.

##  by Kyoung Min Kim
## REFERENCES
[1]Dr. Xiaolei Fang, (2023)ISE789 Lecture note

[2]Yao, F., Müller, H.-G., & Wang, J.-L. (2005). Functional Data Analysis for Sparse Longitudinal Data. Journal of the American Statistical Association








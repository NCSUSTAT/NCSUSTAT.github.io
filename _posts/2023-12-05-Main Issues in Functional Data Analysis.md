---
use_math: true
---

## Sparse(right), fragmented(middle), irregularly sampled data  



![fragmented(middle), sparse(right) data set](/images/sp_img.png)

## Statistical issues in Sparse, fragmented, irregularly sampled data 


The FPC scores $\xi_{ik} = \int (X_i(t) - \mu(t))\phi_k(t) dt$ have traditionally
been estimated by numerical integration, which works
well when the density of the grid of measurements for each
subject is sufficiently large. 

$\hat{\xi}_{ik}=\Sigma_{j=1}^{J} (s_i(t_j) - \hat{\mu}(t_j)) \cdot \hat{\phi}_k(t_j) \cdot \Delta t_j$


Where:
- $\Delta t_j = t_j - t_{j-1}$ (assuming regular grid points)
- $\hat{\xi}_{ik}$ are the FPC-scores for observation $i$.


Because in our model the $Y_{ij}$ are available only at discrete random times $T_{ij}$, reflecting the sparseness of the data, the integrals in the definition of the FPC
scores $\xi_{ik}$ accordingly would be approximated by sums, substituting $Y_{ij}$ as defined in (1) for $X_i(T_{ij})$ and estimates $\hat{\mu}(t_{ij})$
for $\mu(t_{ij})$ and $\hat{\phi}_k(t_{ij})$ for $\phi_k(t_{ij})$, leading to $\hat{\xi}_{ik}^{S} = \sum_{j=1}^{N_i}(Y_{ij} - \hat{\mu}(T_{ij})) \hat{\phi}_k(T_{ij})(T_{ij} - T_{i,j-1})$, setting $T_{i0} = 0$. For sparse functional data, $\hat{\xi}_{ik}^{S}$ will not provide reasonable approximations to $\xi_{ik}$, for example, when one has only two observations per subject. Moreover, when the measurements are contaminated with errors, the underlying random process $X$ cannot be directly observed. Substituting $Y_{ij}$ for $X_i(T_{ij})$ then leads to biased
FPC scores. These considerations motivate the alternative PACE method to obtain the FPC scores.



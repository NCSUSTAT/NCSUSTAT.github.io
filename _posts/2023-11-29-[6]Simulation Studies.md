

## Spinal Bone Mineral Density Dataset (Li et al., 2021)
The Spinal Bone Mineral Density dataset, as introduced by Li et al. (2021), serves as a real-world application
of the proposed methodologies. This dataset captures longitudinal measurements of bone mineral density at
various spinal locations. The irregular observation points and sparse nature of the data pose challenges for
conventional statistical methods.

- Irregular Observation Points
The irregularity in the observation points requires the methodologies to adapt to varying data densities and
handle snippets with different temporal resolutions.
Sparse Longitudinal Data
The dataset’s sparsity necessitates robust methodologies capable of deriving meaningful estimates even in
the presence of limited data points.

- Gaps in the Off-Diagonal Regions
Notable gaps in the off-diagonal regions of the covariance structure present challenges for capturing dependencies between non-adjacent time points. Our estimators will be evaluated on their ability to fill these gaps
and provide accurate representations of the underlying covariance surface.


## Simulation and Data Analysis 


![fragmented(middle), sparse(right) data set](/images/fig1.png)

Figure1: Plot of estimated mean of the 3 estimators (PACE, PFBE, SNPTM) under different values of m and n.

From Figure 1, it can be seen that the mean plots under the three estimators show that the performance of PACE, PFBE, and SNPTM methods is influenced by the sample size (n) and the number of time points (m). That’s performance improves as the sample size and number of time points increase. 





![fragmented(middle), sparse(right) data set](/images/fig2.png)

Figure 2: Plot of estimated covariance of the 3 estimators (PACE, PFBE, SNPTM) under different values of m and n.

It can be seen from Figure 2 that the covariance plots under the three estimators show that the performance of PACE, PFBE, and SNPTM methods for covariance estimation is influenced by the sample size (n) and the number of time points (m). That’s their performance improves as the sample size and number of time points increase. 





![fragmented(middle), sparse(right) data set](/images/table.png)

Table 1 summary of relative errors comparing performance of the 3 estimators (PACE, PFBE, SNPTM)

From Table 1, the analysis was run on the Bone Mineral Density dataset on 1000 iterations. As shown, ‘m’ and ‘n’ represent the number of time points and the number of spatial locations respectively.  That’s ‘m’ is the number of points at which the response variable (bone density) is observed and ‘n’ is the number of spatial locations at which the response variable is observed. 
For Mean Estimation (Method: PACE, PFBE): Pace performs well, especially with a large sample size (n=300, m=10, and n=400, m=15). Also, PFBE also provides good estimates, with a notable improvement as the sample size and time points increase. 
For Covariance Estimation (Method: PACE, SNPTM): SNPTM consistently outperforms PACE in terms of relative error in all scenarios. PACE is reasonable, but SNPTM is more accurate. 
The variance of measurement noise provides estimates of the measurement noise variance. Also, the estimation error for the measurement variance performs well in estimating the error showing low relative errors.
In conclusion, SNPTM(SP) seems to be the most robust and accurate estimator for this specific application, providing the lowest relative errors across different scenarios. PACE and PFBE (FOURIER) are also reasonable choices, with performance improving as the sample size and number of time points increase. 


## Strength and Weakness of PFBE, PACE, SNPTM
- PFBE (Piecewise Functional Bayesian Estimation
  - Strengths:
    - Flexibility: Piecewise models can capture complex functional relationships by allowing different functional forms in different regions. It is also useful when the underlying process 
      exhibits different behaviors in distinct regions.
  - Weaknesses:
    - Computational Complexity: It can be computationally intensive, especially for high-dimensional data or complex models.
- PACE (PEnalized Covariance Estimation
  - Strengths: Regularization: Penalized covariance estimation methods, can provide regularization to prevent overfitting and improve generalization to new data.
  - Weaknesses:
    - Tuning Parameters: Performance can depend on the proper choice of regularization parameters, and finding the right values might require some tuning. Again, Penalized methods assume that the 
     underlying covariance structure is sparse, which might not hold in all situations.

## Strength and Weakness of SNPTM
- Strengths of SNPTM: 
  - 1. Tailored for Functional Data: SNPTM is designed specifically for handling functional data, which are characterized by observations in the form of curves or functions. This specialization
       allows SNPTM to account for the unique properties and challenges associated with functional data analysis.
  - 2. Estimation of Covariance and Variance Functions: SNPTM provides a methodology for estimating covariance and variance functions over continuous domains, which is essential for understanding 
       the dependence structure and variability within functional data.
- Weaknesses of SNPTM:
  - 1. Computational Complexity: Depending on the specific implementation and the size of the functional data, SNPTM may involve computational complexity, especially when 
  dealing with large datasets or high-dimensional functional data.
  - 2. Sensitivity to Model Assumptions: Like many statistical methods, SNPTM may be sensitive to the underlying assumptions of the model, and its performance could be influenced by the 
  appropriateness of the assumed correlation structures and other model specifications.





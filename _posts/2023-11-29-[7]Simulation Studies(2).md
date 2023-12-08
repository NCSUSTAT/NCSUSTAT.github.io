




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








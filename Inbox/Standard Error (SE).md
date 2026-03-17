

15-03-2026 21:14

Status: #in_progress

Tags:

# Standard Error (SE)
The *standard error (SE)* measures the **uncertainty of an estimate due to sampling variability**

When we estimate something from data (mean, regression coefficient, correlation, etc.), the estimate would change if we collected a different sample. The **standard error quantifies how much that estimate typically varies across repeated samples**.
## Conceptual idea
Imagine repeatedly sampling datasets from the same population and computing an estimate each time.

You would obtain a distribution of estimates:
$\hat{\theta_{1}},\hat{\theta_{2}},\hat{\theta_{3}},\dots$
$SE(\hat{\theta})$=StdDev of the estimator across repeated samples
## Example
### standard error of the mean
If the estimate is the sample mean $\bar{x}$:
$$
SE(\bar{x})=\frac{{\sigma}}{\sqrt{ n }} 
$$
where
$\sigma$ = population standard deviation
$n$ = sample size
since $\sigma$ is usually unknown, we use the sample standard deviation $s$:
$$
SE(\bar{x})=\frac{{s}}{\sqrt{ n }} 
$$







## My Questions
if its not *mean* but other estimators?
## References


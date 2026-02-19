

12-02-2026 17:42

Status: #in_progress

Tags:

# MAD

its a way to estimate outliers. 
if you use deviation from the mean. the mean is calculated using the outliers themselves. MAD overcome that problem using median.

given $x_{1},x_{2},\dots,x_{n}$
**step 1** - compute median
$m=median(x_{i})$
**step 2** - compute absolute deviations
$d_{i}=|x_{i}-m|$
**step 3** - take median again
$MAD=median(d_{i})$
 **step 5** - scaling
 for Guassian data: $MAD \approx 0.6745\sigma$
 so we scale: $\hat{\sigma}_{robust}=1.4826\times MAD$
 **Z-score**
 $z{i}=\frac{{x_{i}-m}}{1.4826\times MAD}$
 flag anomaly if: $|z_{i}>3|$

### assumptions
- heavy tailed distribution
- non-Gaussian noise
- Gaussian like distribution



## My Questions


## References


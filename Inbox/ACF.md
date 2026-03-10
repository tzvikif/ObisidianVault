

09-03-2026 12:53

Status: #in_progress

Tags:

# ACF

auto-correlation function (with lag k)
in *time series* $y_{1},\dots,y_{t}$ computes the correlation of the elements with lag k

![[acf.png]]

$\rho_k = \frac{\gamma_k}{\gamma_0}$
$\rho_{k}$ - autocorrelation at lag k
$\gamma_{k}$ - autocovariance at lag k
$\gamma_{0}$ - autocovariance at lag 0 (the variance of the series)

$\gamma_0 = \frac{1}{N} \displaystyle \sum_{t=1}^{N} (y_t - \bar{y})^2$

$\gamma_k = \frac{1}{N} \displaystyle \sum_{t=k+1}^{N} (y_t - \bar{y})(y_{t-k} - \bar{y})$

$\rho_k =  \frac{\displaystyle \sum_{t=k+1}^{N} (y_t - \bar{y})(y_{t-k} - \bar{y})}  {\displaystyle \sum_{t=1}^{N} (y_t - \bar{y})^2}$

properties: $-1 \le \rho_k \le 1, \qquad \rho_0 = 1$

## example
![[Pasted image 20260309131016.png]]
the statistic measures how the current value relates to the value k time steps earlier.

### acf_plot

**TODO:**
https://chatgpt.com/share/69aeaee7-9d70-8013-818c-dd21d5d2d439






## My Questions




## References


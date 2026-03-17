

15-03-2026 18:20

Status: #in_progress

Tags:

# ARIMA

the ARIMA is combined of 
- [[ARIMA#AR (autoregressive)|AR]] 
- [[ARIMA#Integration|Integration]]
- [[ARIMA#MA|MA]]

## AR (autoregressive)
$y_{t}$ is correlated to previous samples.
forecast $y_{t}$ based **solely on past values** (called lags)

$$
Y_{t}=\alpha+\displaystyle \sum_{i=p}^{}\phi_{i}Y_{t-i}+e_{t}
$$

AR(p) - using *p* lags for forecasting.
this is **long term memory**. $Y_{t}$ depends even on $Y_{1}$ (though very little)
## Integration
### differencing
how many times do we need to difference to make the data stationary.
stationary test with [[augmented dickey-fuller test]]
  
## MA
$y_{t}$ is correlated to previous errors.
forecast $y_{t}$ based **solely on past errors** (error lags)
$$
Y_{t}=\alpha+\displaystyle \sum_{i=p}^{}\theta_{i}e_{t-i}+e_{t}
$$
MA(p) - using *p* lags for forecasting
 ![[ARIMA1.png]]
 the *solid* line is the true value
 the *dashed* line is the forecast.
 **Note**
 - for the first error we can take the average of the series
 - the dependence of previous observations declines over time -  [[Weak Stationarity|idea of stationarity]]. After time p it disappears. $Y_{t+1}=\alpha+\theta e_{t}+e{t+1}$. no more $e_{t-1}$ (for p=1)
 - thus short time memory
 
## Combine AR and MA
$Y_{t}=\alpha+\phi_{1}Y_{t-1}+\cdots+\phi_{p}Y_{t-p}+\phi e_{t-1}+\cdots+\phi e_{t-q}+e_{t}$
### techniques for selecting models
1. Plotting patterns in correlation ([[ACF]], [[PACF]])
2. Automatic selection techniques
	1. MINIC
	2. SCAN
	3. ESACF


ARIMA(p, d, q)
p - # of AR terms
d - # of first differences
q - # of MA terms

## My Questions


## References


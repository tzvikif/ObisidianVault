

20-02-2025 13:45

Status: #in_progress

Tags:

# Tabular Features time series

- Rolling Statistics
	- Rolling means/std/max over windows
	- Volatility measures
``` python
df['ul_bytes_rolling_mean_10s'] = df['mean_total_ul_bytes'].rolling(window=10).mean()
df['dl_bytes_volatility'] = df['mean_total_dl_bytes'].rolling(window=5).std() / df['mean_total_dl_bytes'].rolling(window=5).mean()
```
 
## My Questions


## References


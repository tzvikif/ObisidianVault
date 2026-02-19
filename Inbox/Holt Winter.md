

19-02-2026 12:16

Status: #in_progress

Tags:

# Holt Winter

- $y_{t}$ = observed value
- $L_{t}$ = level
- $T_{t}$ = trend
- $S_{t}$​ = seasonal component
- m = season length (e.g., 12 for monthly data with yearly seasonality)
## update equations
### level
$L_t = \alpha (y_t - S_{t-m}) + (1 - \alpha)(L_{t-1} + T_{t-1})$
### trend
$T_t = \beta (L_t - L_{t-1}) + (1 - \beta) T_{t-1}$
### seasonality
$S_t = \gamma (y_t - L_t) + (1 - \gamma) S_{t-m}$
### Forecast h steps ahead
$\hat{y}_{t+h} = L_t + hT_t + S_{t+h-mk}$
$\text{where } k = \left\lfloor \dfrac{h-1}{m} \right\rfloor$


## My Questions


## References


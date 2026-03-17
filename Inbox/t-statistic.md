

15-03-2026 21:28

Status: #in_progress

Tags:

# t-statistic
The *t-statistic* measures how far an estimate is from the value assumed by the [[null hypothesis]], measured in units of [[Standard Error (SE)#Conceptual idea|standard error]].
$$
t=\frac{{estimate-hypothesized\;value}}{SE}
$$
for *SE* see [[Standard Error (SE)]]
**numerator** - How far is the estimate from what the null hypothesis claims?
for example:

| context     | num hypothesis      | numerator         |
| ----------- | ------------------- | ----------------- |
| mean test   | $H_{0}:\mu=\mu_{0}$ | $\hat{x}-\mu_{0}$ |
| correlation | $H_{0}:\rho=0$      | $r-0$             |
So the numerator is simply the difference between the **observed estimate** and the **hypothesized parameter value**.

$$
t=\frac{signal}{noise}
$$
- numerator = signal (observed deviation)
- denominator = noise (sampling variability)
## Example

### mean test
suppose we test
$$
H_{0}:\mu=100
$$
sample mean:
$$
\hat{x}=108
$$
then the numerator is $108-100=8$
The sample mean is 8 units above the value predicted by the null hypothesis.

### another example
- estimate = 5
- null value = 0
- standard error = 5
the nominator is $5-0=5$ 5 units away from the value predicted by the null hypothesis
t-statistic is $t=\frac{5}{5}$
The estimate is 1 *standard error* away from the null hypothesis value
If estimates typically fluctuate by about **1 standard error** just due to sampling noise, then observing a value **1 SE away from the null** is **not unusual**
that why measure in [[Standard Error (SE)|SE]] steps

| t   | approximate p-value |
| --- | ------------------- |
| 0   | 1.0                 |
| 1   | $\approx 0.32$      |
| 2   | $\approx 0.05$      |
| 3   | $\approx 0.003$     |

## My Questions


## References


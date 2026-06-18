

14-06-2026 10:33

Status: 

Tags:

# Exponential Distribution

## use case
i have a store and 5 customers are arriving every minute. 
parameters: the rate ($\lambda$) is 5.
$X\sim EXP(\lambda)$
$X$ - **the time until the next event happens**
$x$ - the possible value of waiting time until an even happend(in that case a customer arrives)

the *PDF* :
$$
f(x)=
\begin{cases}
\lambda e^{-\lambda x}, & x \ge 0 \\
0, & x < 0
\end{cases}
$$
### Expectation
**intuition**: 5 clients per minute. that means that i'l wait (in Expectation) $\frac{1}{5}$
minutes for a customer to arrive.
$\frac{1}{\lambda}$

## My Questions


## References


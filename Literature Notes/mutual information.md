

2024-07-17 11:19

Status:

Tags:

## mutual information

Mutual information is a measure of the mutual dependence between two variables.
It quantifies the amount of information obtained about one random variable through observing the other random variable
if we have random variable X and Y.
and i know the distribution of X if the MI is high i'l know much about the distribution of Y as well.
### Definition

For two random variable $X$ and $Y$, the mutual information$I(X;Y)$ is defined as
$I(X;Y)=\sum_{x\in X}\sum_{y\in Y}p(x,y)\log\left( \frac{p(x,y)}{p(x)p(y)} \right)$

properties:
$$
I(X;Y)\geq 0
$$
$$
I(X;Y) = I(Y;X)
$$
$$
I(X;Y) = H(X) + H(Y) - H(X,Y)
$$

H is the [[Entropy]]



## References




2024-09-23 18:01

Status: 

Tags: #stat

# Binomial Distribution

ההתפלגות מתאימה למקרה בו יש N נסיונות וכל אחד עם הסתברות $p$ של הצלחה , $1-p$ לכשלון
ה PMF מודד את ההסתברות עבור כל מספר ההצלחות K



$Pr(X=k)=$ $\left( \begin{array}{c} {n} \\ {k} \end{array} \right)p^kq^{n-k}$
for $k=0,1,2,\ldots,n$
where $\left( \begin{array}{c} {n} \\ {k} \end{array} \right)=\frac{n!}{k!(n-k)!}$
$p$ is the probability of success.
$1-p$ is the probability of failure.

$X$ is a [[random variable]]



## PMF

![[Binomial Distribution PMF1.png]]

![[Binomial Distribution PMF2.png]]


## Expectation

$\mathbb{E}[X]=N\cdot f$
### Proof
**Lemma**
if $X_{1}, X_{2},\dots, X_{n}$ are independent *Bernoulli(p)* random variables, then the random variable $X$ defined by $X=X_{1}+ X_{2}+\dots+ X_{n}$ has a *Binomial(n,p)* distribution.
$\mathbb{E}[X_{1}+X_{2}+\dots +X_{N} ]=\mathbb{E}[X_{1}]+\mathbb{E}[X_{2}]+\dots + \mathbb{E}[X_{N}]$


for every $X_{i}$ 
$\mathbb{E}[X_{i}]=f\cdot 1 + (1-f)\cdot 0 = f$
$\Rightarrow \mathbb{E}[X]=N\cdot f$
## Variance

$Var[X]=N\cdot f\cdot (1-f)$




## References

https://www.probabilitycourse.com/chapter3/3_1_5_special_discrete_distr.php
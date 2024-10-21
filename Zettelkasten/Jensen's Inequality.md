

2024-07-17 13:50

Status: #in_progress

Tags:

# Jensen's Inequality

given a *convex function* $f$ and a random variable $X$
then:
$$f(\mathbb{E}[X]) \leq \mathbb{E}[f(X)]$$

## Convex function
### definition 1
the tangent is *under* $f$
![[Jensen's_Inequality_convex1.png|400]]

### definition 2
if we draw a line between 2 points in the Epigraph(the space above the function)
all the lines along that line are also in the Epigraph.
![[Jensen's_Inequality2.png|400]]

### the Idea
the yellow lines represent the probabilities. the more dense lines , the more probable that value will occur.
![[Jensen's_Inequality1.png]]

### Proof
lets draw tangent $h(x)$ to $f$ at $\mathbb{E}[X]$ (white dot, which is at $x=3.5$)
in that example $X$ is a random variable that represent the score of the dice.
$x\in\{1,2,3,4,5,6\}$
![[Jensen's_Inequality_proof1.png|400]]
because $f$ is convex every point $f(x)$ is above $h(x)$ 
(at $x=\mathbb{E}[X]$  $h=f$)
therefore $\mathbb{E}[f(x)]\geq \mathbb{E}[h(x)]$
$\mathbb{E}[h(x)]=?$

at $x=\mathbb{E}[X]$ , $h(x)=f(\mathbb{E}[X])$
if we change $x$ , the delta of the change in $x$  is $x-\mathbb{E}[X]$
$\implies h(x)=f(\mathbb{E}[X]) + b\cdot (x-\mathbb{E}[X])$ , $b$ is the slope of $h$
$=f(\mathbb{E}[X])-b\cdot\mathbb{E}[X] + bx)$ 
*according to the definition of Expectation*
$\mathbb{E}[h(x)]=\displaystyle \sum_{i}^{} \left[f(\mathbb{E}[X])-b\cdot\mathbb{E}[X]+bx_{i}\right] \cdot p_{x}(x_{i})$
$=\displaystyle \sum_{i}^{}f(\mathbb{E}[X])\cdot p_{x}(x_{i})\displaystyle -\sum_{i}^{}b\cdot\mathbb{E}[X]\cdot p_{x}(x_{i})+\displaystyle \sum_{i}^{}bx_{i}\cdot p_{x}(x_{i})$
$=f(\mathbb{E}[X])\cdot\displaystyle \sum_{i}^{} \overbrace {p_{x}(x_{i})}^{1}\displaystyle -b\cdot\mathbb{E}[X]\cdot \sum_{i}^{} \overbrace {p_{x}(x_{i})}^{1}+\displaystyle b\sum_{i}^{} \overbrace {x_{i}\cdot p_{x}(x_{i})}^{\mathbb{E}[X]}$
$=f(\mathbb{E}[X])-b\cdot\mathbb{E}[X]+b\cdot\mathbb{E}[X]=f(\mathbb{E}[X])$
$\implies f(\mathbb{E}[X]) \leq \mathbb{E}[f(X)]$



## References

https://www.youtube.com/watch?v=-OjAQDYYAro&t=310s




2024-10-18 01:11

Status: 

Tags: #video

# Maximum Likelihood Data Science Concepts(MLE)

^7c52d1



the problem we are going to solve is if a student will get excepted to a University he wants.

$\left[ \begin{array}{c} {-X-} \\ {.} \\ {.} \\ {.} \end{array} \right]_{{n\times p}}$, $\left[ \begin{array}{c} {y} \\ {.} \\ {.} \\ {.} \end{array} \right]_{{n\times 1}}$
## Model Example

we use [[logistic regression]] as our model.
![[logistic regression#Logit]]

so basically we have to find the $\vec{\beta}$ that fits best the data.

for any student $x_{i}$:
$p(Accept)=\dfrac{e^{\beta^{T}x_{i}}}{1+e^{\beta^{T}x_{i}}}=\dfrac{e^{y_{i}\cdot\beta^{T}x_{i}}}{1+e^{\beta^{T}x_{i}}}$, $y_{i}=1$

$p(Reject)=\dfrac{1}{1+e^{\beta^{T}x_{i}}}=\dfrac{e^{y_{i}\cdot\beta^{T}x_{i}}}{1+e^{\beta^{T}x_{i}}}$, $y_{i}=0$ המשלים של התקבל

$\underbrace{p(y_{i}|x_{i},\beta)}_{likelihood} =\dfrac{e^{y_{i}\cdot\beta^{T}x_{i}}}{1+e^{\beta^{T}x_{i}}}$
>The Probability of observing actual $y_{i}$ given student $x_{i}$ and $\beta$

## Extending to all students
That *logistic regression* Model is just an example, any Model will work.
we want the Model to be as close as possible to the real world.
if a student is Accepted we want $p(y_{i}=1|x_{i},\beta)$ to be high.
if a student is Rejected we want $p(y_{i}=0|x_{i},\beta)$ to be high.
The likelihood above used a single student. How do we extend that idea to all students?

**Assumption** : every student is Independent of the other students. meaning if student $x_{i}$ has Accepted it doesn't have an effect of the other students.
>What is the probability of seeing all the outcomes 

using the *independent* assumption we can multiply all individual probability.
$\mathbb{}$
$\mathcal{L}(y|x,\beta)=p(y_{1}|x_{1},\beta)\cdots p(y_{n}|x_{n},\beta)$
the **goal** is to find $\beta$ such that it *maximize* $\mathcal{L}(y|x,\beta) \Leftrightarrow$ the prediction of the model will be close to the ground truth.


for numerical stability we use *log*
$\log {\mathcal{L}(y|x,\beta)}=$$\displaystyle \sum_{i=1}^{n} p(y_{i}|x_{i},\beta)=\displaystyle \sum_{i=1}^{n}\log e^{y_{i}\cdot\beta^{T}\cdot x_{i}}-\displaystyle \sum_{i=1}^{n}\log (1+e^{\beta^Tx_{i}})= \displaystyle \sum_{i=1}^{n}y_{i}\beta^{T}x_{i}-\displaystyle \sum_{i=1}^{n}\log (1+e^{\beta^Tx_{i}})$
**and that's it basically!**
### to solve our private case model:
in our case the model is relative simple thus we can analytically compute the $\beta$ by taking the derivatives.

$\frac{ \partial \log \mathcal{L} }{ \partial \beta^{T}}=\displaystyle \sum_{i=1}^{n}y_{i}x_{i}-\displaystyle \sum_{i=1}^{n}\sigma(x_{i},\beta)\cdot x_{i}=\underbrace{ \underbrace{x^{T}}_{p\times n}(\underbrace{y}_{n\times 1}-\underbrace{\sigma(x,\beta)}_{n\times 1})}_{n\times 1}$
S.T $\sigma(x_{i},\beta)=p(y_{i}=1|x_{i},\beta)$ 
>why??

we set the derivative to 0 to find $\beta$
$x^{T}(y-\sigma(x,\beta))=0$

## Definition
the Problem we are solving i.e finding the $\beta$ is called the *maximum likelihood problem*
the $\beta$ are called the  *maximum likelihood estimator* (MLE)

## Solution
there is no closed form to solve that problem.
nevertheless we can use neural network using *gradient descent* algorithm and [[EM algorithm|Expectation and Maximization algorithm]]


## References

https://www.youtube.com/watch?v=VOIhswqFWVc
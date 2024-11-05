

2024-10-19 23:05

Status: #in_progress

Tags: #video

# Random Variable

## Definition

a *random variable* $X$ is a function from the sample space to a real numbers
$$X:\Omega\to \mathbb{R}$$
כאשר $\Omega$ היא אוסף של מאורעות.
>$Z$ is a function on $\Omega$



## Example1

נסתכל על ניסוי של זריקת 2 קוביות הוגנות כל אחת בעלת 4 פיאות.
![[Random variable_omega.png|400]]
we call each event  $\omega$. $p(\omega)=\frac{1}{16}$

 we are interested in the sum the two dices.
 Let $Z$ be the sum. $Z$ connects a collection of event to a number.
 ![[Random variableZ.png|400]]
$Z:\Omega\to\{2,3,4,5,6,7,8\}$
- we can look at $Z$ as a set. $\{Z=5\}=\{\omega:Z(\omega)=5\}$. all the events that sums to 5. (the green events)
- $Z$ is not *random* but the events in $\Omega$ are. We call $Z$ *random* variable because the events in $\Omega$ are random. random input yields to random output.
**9:20**
$Z(\omega)=X_{1}(\omega)+X_{2}(\omega)$
## Example2

we toss a coin 5 times. 
$S=\{TTTTT,TTTTH, \dots , HHHHHH\}$
sample space has $2^5=32$ elements.
נניח שאנחנו מעוניינים במספר ה"עץ" שקיבלנו.
נוכל להגדיר משתנה רנדומי שיספור את מספר ה"עץ" שהתקבל.
in that experiment  $X \in \{0,1,2,3,4,5\}$
- $X$ assigns the value 0 to the outcome $\{TTTTT\}$
- $X$ assigns the value 1 to the outcome $\{HTTTT\}$
- $X$ assigns the value 1 to the outcome $\{THTTT\}$
- $\dots$
- $X$ assigns the value 5 to the outcome $\{HH H H H \}$

## References

https://www.youtube.com/watch?v=KQHfOZHNZ3k&t=359s
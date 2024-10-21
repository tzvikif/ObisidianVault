

2024-10-19 23:05

Status: #in_progress

Tags:

# random variable

## Intuition

we have a *random experiment* (coin tossing, cube throwing, success in a test,...)
and we want to analyze it. to help to do that we use *random variable*s
for example in a soccer game which we consider as a *random experiment* we are interested in the number of:
- goals
- shots
- shots on goals
- fouls
each of the results of the above can give us some information about the outcome of the random experiment.


## Example

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

## Definition

a *random variable* $X$ is a function from the sample space to the real numbers
$$X:S\to R$$
כאשר $S$ היא אוסף של מאורעות.
$R_{x}$ is the set of possible value of $X$
in the above example $R_{x}=\{0,1,2,3,4,5\}$
## References


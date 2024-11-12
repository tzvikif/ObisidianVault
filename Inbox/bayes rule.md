

02-11-2024 20:36

Status: #in_progress

Tags: #stat

# Bayes Rule


$p(\omega_{j}|x)=\frac{p(x|\omega_{j})\cdot p(w_{j})}{p(x)}=\frac{p(x|\omega_{j})\cdot p(w_{j})}{ \sum_{\omega_{i}}p(\omega)\cdotp(x|\omega_{i})}$

## Example Classes

we have two classes
- Math
- Philosophy

0.3 of the math students are happy.
0.8 of the Philosophy class are happy.
and we are told that Math class has 100 students
and Philosophy class has 10 students.

if i encounter a happy student what is the probability that he's from math class?
$p(happy|Math)=0.3$
$p(happy|Philosophy)=0.8$
$p(Math)=\frac{100}{110}\approx0.9$
$p(Math)=\frac{10}{110}\approx0.09$

$p(Math|happy)?$
$p(Math|happy)=\frac{p(happy|Math)\cdot p(Math)}{p(happy)}=$
$=\frac{p(happy|Math)\cdot p(Math)}{p(Math)\cdotp(happy|Math)+p(Philosophy)\cdotp(happy|Philosophy)}=\frac{0.9\cdot 0.3}{0.3\cdot 0.9+0.09\cdot 0.8}\approx 0.79$

## Example Vaccination test






## References


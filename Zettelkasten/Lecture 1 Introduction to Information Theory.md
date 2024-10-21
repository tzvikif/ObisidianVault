

2024-09-23 16:58

Status: 

Tags: #video

## Lecture 1 Introduction to Information Theory

אנחנו מדברים במקרה של שידור וקליטה. והקליטה היא לא מה ששודר אלא בתוספת רעשים.
Received Signal $\approx$ Transmitted Signal + Noise
we would like Received Signal = Transmitted Signal 

we'll use **System solution**. we add redundant information to cancel the *noise*.

[[IntroductionToInformationTheory1.excalidraw]]

the DECODER infers n(noise) and s(message)

we'll start with toy model *binary symmetric channel*  [[IntroductionToInformationTheory1.excalidraw]]

<u>Q1</u>
a file of N=10,000 bits are stored , then read. 
roughly how many bits are flipped?
p=0.1 is the probability that a bit flips.

<u>A1</u>
we can make use of [[Binomial Distribution]] with n=10, and p=0.1

$E[X]=N\cdot p$ = 1000
variance = $N\cdot p \cdot q$ = 9000 = $\sigma^2$
$\sigma$ = 30
answer: 1000 $\pm$ 30 

<u>Q2</u>
for a saleable 1 Gb disk drive how small does f need to be
lets assume 5 years of use 1Gb per day.
that is $(5\times365days\times(8\times10^9bits))$ $\approx$ $10^{13}$
if we want that just 1% will complain(first 100 customers will be happy) then $f=10^{-15}$

### Example encoders

- parity coding [[IntroductionToInformationTheory1.excalidraw]]
- repetition code [[IntroductionToInformationTheory1.excalidraw]]
$s$ sender , $r$ receiver
using *bayes theorem*
 $p(s|r)=\frac{p(r|s)\cdot p(s)}{p(r)}$
if 
$p(s=0)=\frac{1}{2}$ , $p(s=1)=\frac{1}{2}$
then
$p(s=1|r=011)=\frac{p(r=011|s=1)\cdot p(s=1)}{p(r=011|s=0)+p(r=011|s=1)}=\frac{(1-f)^{2}\cdot f \cdot \frac{1}{2}}{f^2(1-f)\frac12+(1-f)^2f\frac12}=(1-f)=0.9$
$p(s=0|r=011)=\frac{(1-f)\cdot f^{2} \cdot \frac{1}{2}}{p(r|s=0)+p(r|s=1)}=\frac{(1-f)\cdot f^{2} \cdot \frac{1}{2}}{f^2(1-f)\frac12+(1-f)^2f\frac12}=f=0.1$

$p(s=1|r=001)=\frac{p(r=001|s=1)\cdot p(s=1)}{p(r=001|s=0)+p(r=001|s=1)}=\frac{(1-f)\cdot f^{2} \cdot \frac{1}{2}}{f^2(1-f)\frac12+(1-f)^2f\frac12}=f=0.1$
$p(s=0|r=001)=\frac{p(r=001|s=0)\cdot p(s=0)}{p(r=001|s=0)+p(r=001|s=1)}=\frac{(1-f)^{2}\cdot f \cdot \frac{1}{2}}{f^2(1-f)\frac12+(1-f)^2f\frac12}=(1-f)=0.9$

**conclusion:** if we get 001 we should guess that 0 was sent(0.9 probability).
we can repeat that for all 8 $r$ possible answers.

### how well does that DECODER perform

 [[IntroductionToInformationTheory1.excalidraw]]

in order to achieve a DECODER with $10^{-15}$ bit error. with should use $N_{61}$ (61 repetitions) 

### 7,4 Hamming Code
back to parity DECODER.
[[IntroductionToInformationTheory1.excalidraw]]
succeeds with 1 flip to get s.

### Channon
Chanon found lower bound to the Rate(**C**apacity)! 
![[Pasted image 20240926112638.png|400]]

in our case
$C_{BSC}f = 1- H_2(f)$
$H_{2}(f)=f\cdot log_{2}\frac1f+(1-f)\cdot log_{2}\frac{1}{1-f}\approx 0.53$
meaning we can achieve an error $\to 0$ by about 0.53 rate. (using 2 disk drives instead of 61)

problem for next lecture

![[Pasted image 20240926115105.png]]
## References

https://www.youtube.com/watch?v=BCiZc0n6COY&list=PLruBu5BI5n4aFpG32iMbdWoRVAA-Vcso6&index=1&t=982s

link to the book
https://github.com/florist-notes/CS228_PGM/blob/master/books/Information%20Theory%2C%20Inference%2C%20and%20Learning%20Algorithms%20by%20David%20J.%20C.%20Mackay.pdf
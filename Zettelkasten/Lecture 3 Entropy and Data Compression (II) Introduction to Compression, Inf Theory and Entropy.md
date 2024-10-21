

2024-10-01 13:54

Status: 

Tags: #video

# Lecture 3 Entropy and Data Compression (II) Introduction to Compression, Inf Theory and Entropy

## Source coding theorem
N outcomes from a source X can be compressed into roughly $N \cdot H(X)$ bits.
## Sixty-three game

^99a858

$x \in\{0,1,2,3,\dots ,63\}$
for yes, no question find a specific number.
[[IntroductionToInformationTheory3.excalidraw]] (1)

Total Shanon information content gained = 6 bits.
the string $c_{1}\dots c_{6}$ is an encoding of $x$ - $c(x), c(42)=101010$
every question has 50% of answer.
$h(c_{i})=\log_{2} \frac{1}{p(c_{i})}=\log_{2}2=1$ bit
to give $S$ possible outcomes -> we need  $\lceil \log_{2}S\rceil$ bits.

## Submarine game
 there are  64 squares. we have to guess where the submarine is.
 *before any selection*  
 $P(y)=\frac{1}{64}=0.015$ chance of *y*es(find the submarine)
 $P(n)=\frac{63}{64}=0.984$ *n*o(missed). 
 Entropy=$0.116$
 Information learnt = $0.0$
![[Pasted image 20241006210704.png]]

we got a *no*
 $P(r_{1}=n)=\frac{63}{64}$
$h(r_{1}=n)=\log_{2} \frac{64}{63}$ bits (*Channon information content*)
 ![[Pasted image 20241006211421.png]]

$P(r_{2}=y)=\frac{1}{63}$
$P(r_{2}=n)=\frac{62}{63}$
Entropy=$0.117$
![[Pasted image 20241006212610.png]]

we got a *no*
$P(r_{2}=n)=\frac{62}{63}$
$h(r_{2}=n)=\log_{2}\frac{63}{62}$
![[Pasted image 20241006213340.png]]

$h_{total}=\log_{2} \frac{64}{63}+\log_{2} \frac{63}{62}+\dots+\log_{2} \frac{33}{32}=1.0$ bits
asking is the submarine in the  $1st,$ $2nd, \dots , 32th$ square
is equivalent to asking is it in the $1st$ 32 squares. *yes/no* answer which requires a single bit.
![[Pasted image 20241006214125.png]]

we got a *yes*
$P(r_{44}=y)=\frac{1}{20}$
$h(r_{44}=n)=\log_{2}{20}=4.3$ bits
![[Pasted image 20241006215456.png]]

lets sum all the terms
$h_{total}=\overbrace{\log_{2} \frac{64}{63}+\log_{2} \frac{63}{62}+\dots+ \log_{2} \frac{33}{32}}^{1bit}+{\log_{2} \frac{32}{31}\dots+\log_{2} \frac{21}{20}}+  {\log_{2} 20}=$

$=\log_{2}64-\cancel{\log_{2}63}+\cancel{\log_{2}63}-\cancel{\log_{2}62}+\dots+\cancel{\log_{2}21}-\cancel{\log_{2}20}+\cancel{\log_{2}20}=\log_{2}64=6 bits$
## The Bent Coin Lottery
![[Pasted image 20241006224922.png]]

**Answer 1**
the ticket $000\dots 0$
which make sense hence $P(x=000\dots 0)=\overbrace{0.9\cdot 0.9\cdots 0.9}^{1000}=0.9^{1000}$
has the biggest probability.


**Answer 2**
  $Mean=N\cdot P_{1}=1000\cdot 0.1=100$
 $\sigma=\sqrt{n\cdot p\cdot(1-p)}=\sqrt{1000\cdot 0.1\cdot (0.9) }\approx 10$
 so we take all the tickets from $\overbrace{00 \dots 0}^{zero, ones}, \dots\overbrace{00 \dots 0}^{120, ones}$
 we take 2 std. from the mean. we'll get 95%.
 we add the left tail.
 that will give us 97.5%. 
 Adding some more tickets to get 99% , untill $\overbrace{00 \dots 0}^{123, ones}$
 
$\left( \begin{array}{c} {1000} \\ {0} \end{array} \right)+\dots+\left( \begin{array}{c} {1000} \\ {123} \end{array} \right)\approx2^{530}$

### Encoder - Decoder
What we are left with , are $2^{530}$ tickets which represent 99% of all the tickets.
we can represent every ticket with a unique id whose length is $\lceil \log_{2}2^{530} \rceil \approx 530$ bits
instead of 1000 bits.
that example shows how we can use that technique as *encoder - decoder*

we have the approximation:
$\left( \begin{array}{c} {N} \\ {r} \end{array} \right)\approx 2^{NH_{2}\left( \frac{r}{N} \right)}=2^{1000\cdot( \frac{123}{1000}\cdot \log_{2} \frac{1000}{123}+\frac{877}{1000}\cdot \log_{2} \frac{1000}{877})  }=2^{538}$
## H.W
prove (see book p. 14)
$\log \left( \begin{array}{c} {N} \\ {r} \end{array} \right)\approx NH_{2}\left( \frac{r}{N} \right)$

## References

https://www.youtube.com/watch?v=0SxJl5G2bp0&list=PLruBu5BI5n4aFpG32iMbdWoRVAA-Vcso6&index=3



2024-10-17 20:57

Status: #in_progress

Tags: #video, #consume

# Lecture 4 Entropy and Data Compression (III) Shannon's Source Coding Theorem, Symbol Codes

a *map of symbols* $x \to c(x)$ , $c(x)\in\{0, 1\}^+$ 
we encode $x_{1},x_{2},\dots,x_{N}$ as $c(x_{1}),c(x_{2}),\dots,c(x_{N})$

### Example
a, 1, b 010, c 1011
cabb $\to$ 10111010010

- **How well might a symbol code perform?**
- **How to we make optimal symbol code?**

the *Expected length of a code C for an ensemble X* :
(ensemble X is the symbols with its probabilities)
$L(C,X)=\displaystyle \sum_{i}p_{i}l_{i}$      , $l_{i}=length(c(a_{i}))$
### Example
$A_{x}=\{a,b,c,d\}$
$P_{x}=\{\frac{1}{2}, \frac{1}{4}, \frac{1}{8}, \frac{1}{8}\}$
$H(X)=\frac{1}{2}\times 1+ \frac{1}{4} \times 2 + \frac{1}{8} \times 3 + \frac{1}{8} \times 3=1 \frac{3}{4}$bits

## Rules
- decode correctly
	- uniquely decodable. i.e. for any $\bar{x}, \bar{y} ~[\bar{x}\ne\bar{y}]: C(\bar{x})\ne C(\bar{y}))$. $\bar{x}=concatination ~of ~x_{1}x_{2}\dots$  and $C(\bar{x})=C(x_{1})C(x_{2})\dots)$
- "Easy" to decode
- small $L(C,X)$ (expected length) 

$C_{6}=\{1, 01, 001, 000\}$
$L=1 \frac{3}{4}=H$
caab$\to$ 0011101

### why don't we assign the max length to least prob. code?
### Answer
$\{\frac{1+\epsilon}{4},\frac{1+\frac{\epsilon}{2}}{4},\frac{1-\frac{\epsilon}{2}}{4},\frac{1+\epsilon}{4}\}$
if we use $c_{6}$ $\to L=\frac{9}{4}=2 \frac{1}{4}$ bits 
whereas if we use equal length 4 we'll get 2 bits. 

## Symbol coding supermarket

| L   | 1   | 2   | 3   |
| --- | --- | --- | --- |
| #   | 2   | 4   | 8   |
cost: $2^{-l}$

if a code is uniquely decodable then $\displaystyle \sum_{i}2^{-l_{i}} \le 1$ *Kraft inequality*
instead of
![[Lecture 4 Entropy and Data Compression (III) Shannon's Source Coding Theorem, Symbol Codes.png|400]]
we could take 000 instead of 0001 which will make the $L(C,X)$ shorter

this one gets over the budget.
![[Lecture 4 Entropy and Data Compression (III) Shannon's Source Coding Theorem, Symbol Codes-1.png|400]]
it violates the *Kraft inequality*. so it can't be uniquely decodable.

optimal code
![[Lecture 4 Entropy and Data Compression (III) Shannon's Source Coding Theorem, Symbol Codes-2.png|400]]

the inverse of the previous image
![[Lecture 4 Entropy and Data Compression (III) Shannon's Source Coding Theorem, Symbol Codes-3.png|400]]
which is also optimal. but harder to decode. $1$ is prefix of $10$

A *complete code* is one that has $\displaystyle \sum_{i}2^{-l_{i}}=1$
## Theoretical question

$L(C,X)=\displaystyle \sum_{i}p_{i}l_{i}$
we'll show that the *entropy* is the shortest $L$

Define *ideal length* $l^{*}_{i}=\log_{2} \frac{1}{p_{i}}=h_{i}$

*41:00*







## References

https://www.youtube.com/watch?v=eHGqNvkL4n4&list=PLruBu5BI5n4aFpG32iMbdWoRVAA-Vcso6&index=4

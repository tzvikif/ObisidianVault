

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
*12:30*

## References

https://www.youtube.com/watch?v=eHGqNvkL4n4&list=PLruBu5BI5n4aFpG32iMbdWoRVAA-Vcso6&index=4

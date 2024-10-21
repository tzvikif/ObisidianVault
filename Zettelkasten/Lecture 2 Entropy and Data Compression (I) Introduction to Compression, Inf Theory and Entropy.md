

2024-09-26 11:53

Status: 

Tags: #video 
## Lecture 2 Entropy and Data Compression (I) Introduction to Compression, Inf Theory and Entropy

review:
according to **Shannon's noisy channel coding theorem**
*we don't need to add "much" redundancy in order to achieve reliable channel.* which will be proved later in the course.

in usual we have redundancy in the data(Jane Austin text). to be more efficient
we'll use *compressor* & *Decompressor*

## Find the "bad" ball
[[IntroductionToInformationTheory2.excalidraw]]
According to Shannon we should follow the maximum Entropy to make as weights as possible. $\implies$ uniform probability.
## Bent coin

outcome $x\in \{Tails, Heads\}$
probabilities $\{0.9, 0.1\}$
$P(x=Tails)=0.9$



![[Pasted image 20241001115752.png|500]]

[[shannon information content of an outcome]] tells us how much information we gain(in bits) if an even occurred. 
from  the image above we can see that we gain more information from the *Head* event. 

### H.W

a coin with $p_{1}=0.1$ will be tossed $N=1000$ times. The outcome is $x=x_{1}x_{2}\dots x_{N}$.
e.g $x=00001001000100\dots0010$
You can buy any of the $2^{N}$ possible tickets from $1 each, before the coin tossing.
- to have a 99% chance of winning at lowest possible cost, which tickets would you buy?
- how many tickets is that?
Express you answer in the form $2^{(\dots)}$


## References

https://www.youtube.com/watch?v=y5VdtQSqiAI&list=PLruBu5BI5n4aFpG32iMbdWoRVAA-Vcso6&index=2
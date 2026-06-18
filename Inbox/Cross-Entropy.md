

28-11-2024 10:50

Status: #ml , #in_progress 

Tags:

# Cross-Entropy

$H(P,Q)$ - average surprise you will get by *observing* a random variable governed by distribution $P$ (true distribution) , while *believing* (we might be wrong) its model $Q$
TODO: the image is displaying information content not entropy. 
![[Cross-Entropy.png]]
in the image we observe 10 Heads in a row. We assume(we are wrong) the coin is fair i.e the distribution is $p(Head)=0.5, p(Tail)=0.5$ .thus we are very [[Shannon information content of an outcome|surprise]] surprise $h(X)=7$.  if we had known the true distribution our surprise would be much less namely 0.1.
Therefore the model assigns high loss to real observations. That is exactly what **cross-entropy loss** penalizes.
## Definition
$H(p,q)=\mathbb{E}_{x \sim p}[-\log q(x)]$
$CE(P,Q)=\displaystyle \sum_{s}^{states}p_{s}\log\left( \frac{1}{q_{s}} \right)$
the surprise can come from 2 sources:
1. Believing in the wrong model
2. The uncertainty of the data. meaning its distribution. Even if i know the distribution (for example a fair coin) still i have surprise ($h(X)$)

when $P=Q$
$CE(P,Q)=CE(P,P)=\displaystyle \sum_{s}^{states}p_{s}\log\left( \frac{1}{p_{s}} \right)=H(P)$
## Properties
- $H(P,Q) \ge H(P)$. believing in the wrong model can only increase the surprise.
- Asymmetry. $H(P,Q) \ne H(Q,P)$

## Implications
we use the *Cross-Entropy* as $\mathcal{L}oss$ function.
actually we use the [[KL-Divergence]] but the second term(the inherent surprise of  $P$) is constant, because it relies of the merely of the data. so for efficiency reasons we can omit it.

## My Questions


## References


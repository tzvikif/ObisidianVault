

28-11-2024 11:14

Status: #in_progress

Tags:

# KL-Divergence

to quantify the difference from the *observing* distribution $P$ and from the believing *distribution* $Q$ , **omitting** the inherent surprise of the data observing $P$.
$D_{KL}=$ [[Cross-Entropy]] - [[Entropy]]
## Cross-Entropy
![[Cross-Entropy#Definition]]
## Entropy
![[Entropy#Definition]]

$H(P,Q)-H(P)=\displaystyle \sum_{s}^{states}p_{s}\log\left( \frac{1}{q_{s}} \right)-\displaystyle \sum_{s}^{states}p_{s}\log\left( \frac{1}{p_{s}} \right)=$
$=\displaystyle \sum_{s}^{states}p_{s}\log\left( \frac{p_{s}}{q_{s}} \right)=D_{KL}(P,Q)$

## My Questions
**Q**
why subtract $H(P)$ from $H(P,Q)$ ?
**A**
When we define $D_{KL}(P∣∣Q)=H(P,Q)−H(P)$, we're isolating a specific aspect of information theory:
- **$H(P)$ represents the theoretical minimum** number of bits needed to encode data from distribution P (using an optimal coding scheme for P).
- **$H(P,Q)$represents the actual number** of bits needed when we encode data from distribution PP P using a coding scheme optimized for distribution QQ Q.
- **The difference $H(P,Q)−H(P)$ tells us the extra bits** needed due to using the "wrong" distribution (Q instead of P).
It isolates just the component that measures distributional difference
From an *information-theoretic* perspective, we subtract  $H(P)$ to eliminate the inherent uncertainty in P itself, leaving only the "extra uncertainty" introduced by using Q instead of P.
## References

https://youtu.be/KHVR587oW8I?si=iuesFsrcR8NVAadm

https://claude.ai/share/8a4f8fa2-57e9-4da1-bbc2-2d68b29746b1
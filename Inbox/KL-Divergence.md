

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

in practice to train generative models we need additional mathematical toolbox:
- Latent-variable models
- Variational inference
- ELBO

## References

https://youtu.be/KHVR587oW8I?si=iuesFsrcR8NVAadm

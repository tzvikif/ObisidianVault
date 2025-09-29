

14-09-2025 15:30

Status: 

Tags:

# Mahalanobis distance

given embeddings $\{e_{i}\}_{i=1}^N$ from inlier training data
- compute the **mean vector**
$\mu=\frac{1}{N}\displaystyle \sum_{i=1}^{N}e_{i}$
- compute the **[[covariance]] matrix**
$\Sigma=\frac{1}{N-1}\displaystyle \sum_{i=1}^{N}(e_{i}-\mu)(e_{i}-\mu)^T$
then for a new point $e$ the *Mahalanobis distance* is
$d_{M}(e)=\sqrt{ (e-\mu)\Sigma^{-1}(e-\mu)}$

## My Questions
Why Mahalanobis instead of Euclidean?
- Euclidean distance treats every direction equally whereas  Mahalanobis distance “rescales” the space according to the covariance structure of the inliers: directions with high variance are down-weighted, directions with low variance are up-weighted. This makes it sensitive to unusual directions in latent space, which is exactly what OOD detection needs


## References


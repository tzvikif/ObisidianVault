

2024-07-22 16:58

Status:

Tags:

## GraphLime

### Motivation 

[[GNNExplainer]] mainly focuses on graph structures and not on finding useful
features.

in contrast to [[LIME]]
- using linear model to fit its decision process is unbefitting because of its nonlinearity
Although the
- key component of GraphLIME is nonlinear, its interpretability is mathematically guaranteed


## formulation of GraphLIME Explainer

for each node $v_i$ we have feature vector $x_i$ which every feature is extracted from the real world. and can be understood by humans
we define $g\in G$ as **explanation model** , where G is a class of *interpretable* models such as linear regressions, decision trees etc.
in the paper g is [[Hilbert-Schmidt Independence CriterionLasso (HSIC Lasso)]]

$x_{i}\in \mathbb{R}^{d}$  - is the feature vector of node $v_i$
$X_{n}\in \mathbb{R}^{n \times d}$  - represents the information matrix of node $v$ . where $n$ is the number of neighbors of $v$ and $d$ is the dimension of $x_i$

taking into account $N$ hops from $v$. we obtain $X_{n}=[x_1,x_2,...,x_m]$
$x_{i}$ is the feature vector of $v_i$. $v_{i} \in S_N$ . $S_N$ is the set of N-hop neighbors of the explaining node $v$ and $m$ is the number of N-hop neighbors of $v_i$
the GNN model is $f$ is trained and optimized for the data. we have the prediction $y_i=f(x_i)$ . we can the prediction $y_i$ as label in the explanation model $g$.
### Nonelinear Explanation Model: HSIC LASSO
Hilbert-Schmidt Independence Criterion Lasso

[[GraphLimeExperiments]]
## References

[GraphLIME: Local Interpretable Model Explanations for Graph Neural Networks](https://arxiv.org/abs/2001.06216)




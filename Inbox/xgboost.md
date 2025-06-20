

25-02-2025 11:21

Status: #in_progress

Tags: #ml, #consume

# XGBoost


## Simple Analogy

Imagine you're trying to predict house prices:
1. You start with a basic estimate: "All houses cost the average price of $250,000."
2. You notice this estimate is off by various amounts for different houses.
3. You build a small decision tree that predicts these errors based on location.
4. You update your prediction: "Base price ($250,000) + location adjustment."
5. You still have errors, so you build another small tree that predicts these new errors based on house size.
6. You update again: "Base price + location adjustment + size adjustment."
7. You continue this process, with each new tree focusing on correcting the remaining errors.

### Unique Features of XGBoost
What sets XGBoost apart from standard [[Gradient Boosting]]:
- **Tree Pruning**: Unlike traditional boosting that builds trees level by level, XGBoost builds the tree to a maximum depth, then prunes it backward, removing splits that don't improve the objective function.
- **Handling Missing Values**: XGBoost has a built-in way to handle missing values by learning which direction (left or right branch) is optimal when encountering missing values.
- **Weighted Quantile Sketch**: Efficiently finds the best split points when the dataset doesn't fit in memory.
- **Sparsity-Aware Split Finding**: Optimized algorithm for sparse data structures common in real-world applications.
- **Parallel Processing**: Uses multi-threading to build trees in parallel.
- **Cross-Validation**: Built-in functionality to perform cross-validation at each iteration.
### Weak Learners in XGBoost
XGBoost typically uses shallow decision trees (often called "stumps" when they have just one split) as its base models. Each individual tree is not very powerful on its own.
see [[Weak Learner#Why Weak Learners Work Better|Why Weak Learners Work Better]] here.
### Sequential Improvement
XGBoost builds trees sequentially, where each new tree tries to correct the errors made by the combination of all previous trees.


## Loss function
$\mathcal{L}(\phi)=\sum_il(\hat{y}_i,y_i)+\sum_k\Omega(f_k)$
where $\Omega(f)=\gamma T+\frac{1}{2}\lambda\|w\|^2$
at the $t^{th}$ iteration  
$l({\hat{y}}_i,y_i)$=$l(y_i,\hat{y_i}^{(t-1)}+f_t(\mathbf{x}_i))$

second order Taylor approximation
$\approx l(y_i,\hat{y}^{(t-1)})+g_if_t(\mathbf{x}_i)+\frac{1}{2}h_if_t^2(\mathbf{x}_i)$
$g_i=\frac{\partial\mathcal{L}(y_i,\hat{y}_i^{(t-1)})}{\partial\hat{y}_i^{(t-1)}}$
$h_i=\frac{\partial^2\mathcal{L}(y_i,\hat{y}_i^{(t-1)})}{\partial\hat{y}_i^{(t-1)}}$
### leaf value
$\tilde{\mathrm{Obj}}(f_t)=\displaystyle \sum_{i=1}^n[g_if_t(x_i)+\frac{1}{2}h_if_t^2(x_i)]+\Omega(f_t)$
$\tilde{\mathrm{Obj}}(f_t)=\displaystyle \sum_{j=1}^T\sum_{i\in I_j}[g_iw_j+\frac{1}{2}h_iw_j^2]+\gamma T+\frac{1}{2}\lambda\sum_{j=1}^Tw_j^2$
$\tilde{\mathrm{Obj}}(f_t)=\displaystyle \sum_{j=1}^T\left[w_j\sum_{i\in I_j}g_i+\frac{1}{2}w_j^2\sum_{i\in I_j}h_i\right]+\gamma T+\frac{1}{2}\lambda\sum_{j=1}^Tw_j^2$
for a  fixed tree structure the optimal weight $w^{*}_{i}$ for each leaf $j$
$\frac{\partial Obj}{\partial w_j} = \sum_{i \in I_j} g_i + \left(\sum_{i \in I_j} h_i + \lambda\right) w_j = 0$
$w_j^* = -\frac{\sum_{i \in I_j} g_i}{\sum_{i \in I_j} h_i + \lambda}$
we plug $w^{*}_{i}$ back in the loss function
$\tilde{L}^{(t)}(q) = -\frac{1}{2} \displaystyle \sum_{j=1}^{T} \frac{\left(\sum_{i \in I_j} g_i\right)^2}{\sum_{i \in I_j} h_i + \lambda} + \gamma T$
## Split Evaluation Metric
[[Split Gain]]
$\mathrm{Split~Gain}=\frac{(\sum_\mathrm{left}g_i)^2}{\sum_\mathrm{left}h_i+\lambda}+\frac{(\sum_\mathrm{right}g_i)^2}{\sum_\mathrm{right}h_i+\lambda}-\frac{(\sum_\mathrm{all}g_i)^2}{\sum_\mathrm{all}h_i+\lambda}-\gamma$
where $\lambda$ is the [[L2 regularization]] term and $\gamma$ is a complexity penalty for each leaf.


## Loss Functions in XGBoost
### Regression

### Classification

## Key Terms and Categories Related to XGBoost

### Ensemble Learning Concepts:

1. Boosting
2. Gradient Boosting
3. Weak learners
4. Sequential ensemble
5. Bias-variance tradeoff

### Mathematical Foundations:

1. Loss function
2. Gradient descent
3. Taylor expansion
4. Second-order approximation
5. Regularization (L1/L2)

### Tree-Based Methods:

1. Decision trees
2. Split finding
3. Information gain
4. Leaf weights
5. Tree pruning

### XGBoost Innovations:

1. Sparsity-aware algorithm
2. Weighted quantile sketch
3. Block structure
4. Out-of-core computation
5. Cache-aware access
## My Questions


## References

[https://arxiv.org/abs/1603.02754](<XGBoost: A Scalable Tree Boosting System>)
https://www.youtube.com/watch?v=WzRc9aNfNZ8&t=1291s
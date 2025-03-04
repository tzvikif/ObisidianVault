

03-03-2025 14:47

Status: #in_progress

Tags: #ml 

# Split Gain
## The Concept of Split Gain
Split gain is a fundamental concept in decision tree learning that measures how much "improvement" we get by splitting a node. It helps the algorithm decide:

1. Which feature to split on
2. What threshold value to use for the split
3. Whether to make a split at all
## The Basic Intuition
Imagine you're building a decision tree and need to decide how to divide your data into subgroups. You want these subgroups to be as "pure" as possible, meaning that instances within each subgroup are similar to each other. Split gain quantifies this improvement in purity.
### Example:
If you're predicting whether customers will buy a product:
- Before splitting: 50% yes, 50% no (mixed, unpredictable)
- After splitting by age:
    - Young customers: 80% yes, 20% no (more predictable)
    - Older customers: 20% yes, 80% no (more predictable)

The split gain measures this improvement in predictability.
$\mathrm{Split~Gain}=~\mathrm{Impurity(parent)}-\mathrm{Weighted~ Impurity(children)}$
Where:
- Impurity(parent) is the impurity measure of the node before splitting
- Weighted Impurity(children) is the weighted average impurity of the resulting child nodes
The weighting is based on how many samples go to each child node:
$\mathrm{Weighted~ Impurity(children)}=\frac{N_{left}}{N}\times\mathrm{Impurity(left)}+\frac{N_{right}}{N}\times\mathrm{Impurity(right)}$
## Common Imputiry Measures
- **Gini Impurity** (used in CART, [[Random Forest]])
$\text{Gini}(t) = 1 - \sum_{i=1}^{c} p(i|t)^2$
where:
**t** refers to a specific node in the decision tree.
**c** is the total number of classes
$p(i|t)$ is the proportion of class i instances in node t.
- **[[Enrtopy]]** 
$\text{Entropy}(t) = -\sum_{i=1}^{c} p(i|t) \log_2 p(i|t)$
- Variance (for regression trees)
$\text{Variance}(t) = \frac{1}{N} \sum_{i=1}^{N} (y_i - \bar{y})^2$
Where $y_i$ are the target values and ȳ is their mean
- **Gradient-based measures**(in [[Gradient Boosting]])
	- - Use the gradients of the loss function to measure impurity
	- For example, using squared error of the residuals

parent node impurity
$\text{Impurity(parent)} = \frac{1}{N}\sum_{i=1}^{N}(g_i - \bar{g})^2$
left child impurity
$\text{Impurity(left)} = \frac{1}{N_L}\sum_{i \in \text{left}}(g_i - \bar{g}_L)^2$
right child impurity
$\text{Impurity(right)} = \frac{1}{N_R}\sum_{i \in \text{right}}(g_i - \bar{g}_R)^2$
Weighted impurity of children
$\text{Weighted Impurity(children)} = \frac{N_L}{N}\text{Impurity(left)} + \frac{N_R}{N}\text{Impurity(right)}$
This is the standard formula for variance reduction in a regression tree split:
$\mathrm{Split~Gain}=\frac{N_L}{N}(\bar{g}_L-\bar{g})^2+\frac{N_R}{N}(\bar{g}_R-\bar{g})^2$
## My Questions


## References


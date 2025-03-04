

27-02-2025 12:44

Status: #in_progress

Tags:

# Gradient Boosting

### Real-life analogy
Consider predicting house prices:
- A single decision tree might split houses by neighborhood, then by size, then by age
- In gradient boosting the first tree might focus on neighborhood
- The second tree specifically corrects neighborhood-based errors by looking at house features that weren't captured well by the first model
- The third tree might focus on capturing seasonal market trends that weren't addressed by the previous models
- Each subsequent tree becomes an expert in fixing specific types of errors from the combined previous trees

The final prediction combines all these trees, with each contribution carefully weighted to maximize accuracy while preventing overfitting.

This sequential, error-focused approach is what differentiates boosting methods like [[XGBoost]] from other ensemble methods like [[Random Forest|Random Forests]] (which build trees independently and combine them).

### In Technical terms
1. You start with a simple model (often a shallow decision tree)
2. Identify the errors (residuals) from this model
3. Train a new model to predict these errors
4. Add this new model to the ensemble, with each model getting a weighted contribution
5. Repeat steps 2-4 until performance stops improving

[[Model Ensembling]]

$X\to F(X)$
learn $F(X)$ as sum of M weak learners:
$F(X)=\displaystyle \sum_{i=1}^{M}F_{i}(X)$
1. define loss function $\mathcal{L}(Y,\hat{Y})$
2. Start with $F_{1}(X)=f_{1}(X)=\bar{Y}$ (average of all ground truth)
![[Gradient Boosting.png]]
3. $\hat{r_{1i}}=-\frac{d\mathcal{L}(y_{i},\hat{y_{i}})}{d\hat{y_{i}}}|_{\hat{y_{i}}=F_{i}(x_{i})}$ , do it for all data points $i=1\dots N$
4. Fit new weak learner $\hat{r_{1}}\approx X \Rightarrow f_{2}(X)$ 
5. figure about "how much" of $f_{2}$ to add $\hat{\gamma_{2}}=\underset{\gamma} argmin\left[ \displaystyle \sum_{i=1}^{N}\mathcal{L}(y_{i},f_{i}(x_{i})+\gamma \cdot f_{2}(x_{i})) \right]$
6. $F_{2}(X)=f_{1}(X)+\hat{\gamma_{2}}\cdot f_{2}(X)$
7. return to step 3


### Explanation
lets say we are in step $m+1$
$F_{m+1}(X)=f_{m}(X)+\hat{\gamma}_{m+1}\cdot f_{m+1}(X)$
$\approx F_{m}(X)+\hat{\gamma}_{m+1}\cdot r_{m}=F_{m}(X)+\hat{\gamma}_{m+1}\cdot\frac{d\mathcal{L}(y_{i},\hat{y_{i}})}{d\hat{y_{i}}}$
which is basically *gradient descent*.


## My Questions
- mention several *gradient boosting* and how they work.

## References

[Gradient Boosting : Data Science's Silver Bullet](https://www.youtube.com/watch?v=en2bmeB4QUo&t=434s)

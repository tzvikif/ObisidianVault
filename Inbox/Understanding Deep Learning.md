

27-01-2025 20:39

Status: #in_progress

Tags: #book, #consume 

# Understanding Deep Learning


## Chapter 4


## Chapter 5

### 5.2 Recipe for constructing loss function
The recipe for constructing loss functions for training data $\{x_{i}, y_{i}\}$ using the maximum likelihood approach is hence:
1. Choose a suitable probability distribution $Pr(y|\theta)$ defined over the domain of the predictions y with distribution parameters $\theta$. ($\theta$ could be probability of *biased coin* of the $\mu$ in *Normal distribution*)
2. Set the machine learning model $f[x,\phi]$ and $Pr(y|\theta)=Pr(y|f[x,\phi])$
3. To train the model, find the network parameters $\hat{\phi}$ that minimize the negative
log-likelihood loss function over the training dataset pairs $\{x_{i}, y_{i}\}$:
$\displaystyle \hat{\phi}=\underset{\phi}{\operatorname*{\operatorname*{argmin}}}\left[L[\phi]\right]=\underset{\phi}{\operatorname*{\operatorname*{argmin}}}\left[-\sum_{i=1}^{I}\log\left[Pr(\mathrm{y}_{i}|\mathrm{f}[\mathrm{x}_{i},\phi])\right]\right]$
4. To perform inference for a new test example x, return either the full distribution $Pr(y|f[x,\hat{\phi}])$ or the value where this distribution is maximized.
## My Questions


## References


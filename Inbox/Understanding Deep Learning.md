

27-01-2025 20:39

Status: #in_progress

Tags: #book, #consume 

# Understanding Deep Learning

current: 8.4


## Chapter 4


## Chapter 5
### Maximum Likelihood
we shift of predicting y directly. we consider the model as computing *conditional probability* distribution $Pr(y|x)$. 
### 5.2 Recipe for constructing loss function

 $Pr(y|\theta)$ $\theta$. ($\theta$ could be probability of *biased coin* of the $\mu$ in *Normal distribution*)
1.  machine learning model $f[x,\phi]$ and $Pr(y|\theta)=Pr(y|f[x,\phi])$
2. To train the model, find the network parameters $\hat{\phi}$ that minimize the negative
log-likelihood loss function over the training dataset pairs $\{x_{i}, y_{i}\}$:
$\displaystyle \hat{\phi}=\underset{\phi}{\operatorname*{\operatorname*{argmin}}}\left[L[\phi]\right]=\underset{\phi}{\operatorname*{\operatorname*{argmin}}}\left[-\sum_{i=1}^{I}\log\left[Pr(\mathrm{y}_{i}|\mathrm{f}[\mathrm{x}_{i},\phi])\right]\right]$

## Chapter 9 Regularization
### Explicit regularization
$\displaystyle \hat{\phi} = \underset{\phi} {argmin} \left[ \sum_{i=1}^{I} \ell_i[\mathbf{x}_i, y_i] + \lambda \cdot g[\phi] \right]$
where $g[ϕ]$ is a function that returns a scalar which takes larger values when the parameters are less preferred.
**Probabilistic interpretation**
consider regularization term as prior $Pr(\phi)$. and we now have *maximum a posterioir* or MAP criterion
$\displaystyle \hat{\phi} = \underset{\phi} {argmin} \left[ \prod_{i=1}^{I} Pr(y_{i}|x_{i},\phi) \cdot Pr(\phi)\right]$
after negative log-likelihood
$\lambda \cdot g[\phi]=-\log[Pr(\phi)]$
### equation 9.12: bayesian Prediction
$Pr(y|x, \{x_i, y_i\}) = \int \mathcal{N}(f[x, \phi], \sigma^2) \cdot Pr(\phi | \{x_i, y_i\}) d\phi$
for normal distribution $Pr(y|x, \phi) = \mathcal{N}(f[x, \phi], \sigma^2)$
- **Multiple Predictions**: Instead of one prediction $f[x,ϕ^]f[x, \hat{\phi}] f[x,ϕ^​]$, we get a weighted average over ALL possible parameter values $\phi$
- **Uncertainty Quantification**:
    - **Epistemic uncertainty**: From uncertainty in $\phi$ (captured by $Pr(ϕ∣{xi,yi})Pr(\phi|\{x_i, y_i\}) Pr(ϕ∣{xi​,yi​}))$
    - **Aleatoric uncertainty**: From data noise $\sigma^2$
**Practical Result**:
$E[y|x, \{x_i, y_i\}] = \int f[x, \phi] \cdot Pr(\phi|\{x_i, y_i\}) d\phi$
This is a weighted average of neural network outputs, where weights are posterior probabilities.
**L2 regularization**
**early stopping**
**Ensembling**
**dropout**

## Chapter 10 Convolutional networks

### keys words
- downsampling
- upsampling
- convolution
- deconvolution
- filter
- map
- stride
- image classification
- object detection
- Semantic segmentation
- 
## Chapter 11: Residual network

### Batch Normalization
with residual,  the variance size growth exponentially with the number of the residuals layers.
$f_{1}(x)$
$f_{2}(x+f_{1}(x))$
$f_{3}(f_{1}(x)+f_{2}(x+f_{1}(x)))$



## References


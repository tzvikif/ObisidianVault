

2024-09-10 17:45

Status: 

Tags: #blog

## exploding_vanishing_gradient

### what is Vanishing Gradient?

the gradient get smaller and smaller and eventually at the  lower layers there is nearly not update of the gradient.

![[Pasted image 20240910175138.png|400]]

if $x$ is very big or small there gradient of $\sigma$ is practically zero.
which will change slightly the upper layers and the lower layers won't be updated.

### what is Exploding Gradient?

in some cases the value of the gradient is getting larger. hence any update can change significantly the weights which leads to unstable training. 
and leads to buffer overflow (Nan)

if the weights generate some large loss. the gradient will be large also. 
and will get bigger during the update.

![[Pasted image 20240910182057.png|400]]

### Solutions

- Proper [[Weight Initialization]]
- Using [[Non-saturating Activation Functions]]
- [[Batch Normalization]]
- [[Gradient Clipping]]


## References

[The Challenge of Vanishing/Exploding Gradients in Deep Neural Networks](https://www.analyticsvidhya.com/blog/2021/06/the-challenge-of-vanishing-exploding-gradients-in-deep-neural-networks/)

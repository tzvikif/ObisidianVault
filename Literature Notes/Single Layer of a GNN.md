

2024-07-16 17:16

Status:

Tags: 

GNN Layer = Message + Aggregation
![[Pasted image 20240716172032.png| 400]]

1. we take the messages from the neighbors 
2. aggregate the messages in a function with is order invariant.

## Message computation
![[Pasted image 20240716172946.png|200]]
 we take the features from the neighbors of u and translate it using MSG(e.g linear layer)
 $$
 m_{u}^{l}= W^{l}h_{u}^{(l-1)}
$$
## Aggregation
![[Pasted image 20240716173733.png|400]]

example for aggregation functions: sum, mean, max.

**Issue** : information from the node v itself could get lost. 
so we add the node itself with its own MSG function(B weights matrix)
![[Pasted image 20240716180914.png|200]]
and we get
![[Pasted image 20240716181009.png|450]]

after **Message** and **Aggregation** we execute [[Nonelinearity activation function]]
## References

[Standford cs224w Lecture 7.2](https://www.youtube.com/watch?v=247Mkqj_wRM&list=PLoROMvodv4rPLKxIpqhjhPgdQy7imNkDn&index=22)



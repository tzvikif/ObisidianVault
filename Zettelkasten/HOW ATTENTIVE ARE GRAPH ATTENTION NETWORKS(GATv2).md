

2024-09-01 11:31

Status:

Tags: #paper

## GATv2Conv

An improved version of  [[Graph Attention Networks]]

![[Pasted image 20240915105656.png]]
we define $i$ as the *query* and all the neighbors as *keys*
in the example above $j$
as we can see $e_{ij}$ depends on the
- query $a_1^TW\vec{h}_i$ which takes part in all $e_{ik}$$k\in N_i$ (hence static) 
- keys $a_2^TW\vec{h}_k$ 
the attention rank(*argsort*) of keys depends only on  $a_2^TW\vec{h}_j$ for all queries.
the *key* part doesn't play a role.
*static attention:* if $\forall i$  $a_2^TW\vec{h}_j$ has the highest value. 

![[Pasted image 20240917120250.png]]
in that example $\forall i$ $e_{ij\ne8}$ < $e_{i8}$ 

the main idea is to avoid linearity $e_{ij}=LeakyReLU(a_1^TW\vec{h_{i}}+a_2^TW\vec{h_i})$
instead
$e_{ij}=a^TLeakyReLU(W\cdot[\vec{h_{i}}||\vec{h_i}])$


## References

[How Attentive are Graph Attention Networks?](https://arxiv.org/abs/2105.14491)

https://nn.labml.ai/graphs/gatv2/

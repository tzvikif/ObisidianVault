

2024-09-09 10:24

Status: 

Tags: #paper, #video, #blog

## GAT (Graph Attention Network)

the paper uses the concept introduced in [[Attention Is All You Need]]. 
give an "amount of attention" for each neighbor ,following *self-attention* strategy.

![[Pasted image 20240912120127.png|400]]

every node is linearly transformed with its neighbors.

![[Pasted image 20240912121409.png|600]]

$h=\{\vec{h}_{1}, \vec{h}_{2},\ldots, \vec{h}_{N}\},    \vec{h}_{i}\in\mathbb{R}^F$
$N$ is the number of nodes
$F$ is the number of features.
$W\in\mathbb{R}^{F' \times F}$ (in the image the dimensions are transformed?!)
$h'=\{\vec{h'}_{1}, \vec{h'}_{2},\ldots, \vec{h'}_{N}\}, \vec{h}_{i}\in\mathbb{R}^{F'}$  is the output after the transformation.

we want a weighted sum of all the neighbors. 
$\vec{h}_i'=\sigma(\displaystyle\sum\limits_{j\in{N_{i}}}\alpha_{ij}W\vec{h}_{j})$ , $\alpha_{ij}\in [0,1]$

$e_{ij}$ is attention score 
equation[1]
![[Pasted image 20240912131507.png]]
$\vec{a}$ is a learnable parameter.
|| is concatenation of the vectors
![[Pasted image 20240912132258.png]]

the $\alpha's$ are computed as follows:
$\alpha_{ij}=softmax_{j}(e_{ij})=\frac{exp(e_{ij})}{\displaystyle\sum\limits_{k\in N_i}exp(e_{ik})}$
using equation[1] we get:
$\alpha_{ij}=\frac{exp(LeakyReLu(\vec{a}^T[W\vec{h}_i||\vec{h}_j]))}{\displaystyle\sum\limits_{k\in N_i}exp(LeakyReLu(\vec{a}^T[W\vec{h}_i||\vec{h}_k])))}$

for efficient implementation we use *broadcasting* for computer $e_{ij}$ matrix

![[Pasted image 20240912133024.png]]
from $e_{ij} \to \alpha_{ij}$ 
![[Pasted image 20240912151136.png]]

lets call the above matrix $E$. so to compute the 
in that case the row $i$ is the vector $\alpha_{i}=[\alpha_{i1}, \alpha_{i2},\ldots,\alpha_{iN}]$
$\left[ \begin{array}{ccc} ---\alpha_{1}--- \\ . \\ . \\ . \\ ---\alpha_{i}---\\ . \\ . \\ . \\---\alpha_{N}--- \end{array} \right]_{N\times N}\times\left[ \begin{array}{ccc} ---\vec{h}_1---\\ . \\ . \\ . \\ ---\vec{h}_i---\\ . \\ . \\ . \\ ---\vec{h}_N--- \end{array} \right]_{N\times F'}=M_{N\times F'}$
$M_{N\times F'}$ is the next layer.
### Multiple Heads
for $k$  heads
![[Pasted image 20240912142100.png]]
that means if we have  $k$ heads the number of features will be $k\cdot F'$

![[Pasted image 20240912183855.png|500]]
every color is a *head*. thus we'll have for  $\vec{\alpha}_{12}$ for example 3 sets: $\vec{\alpha}_{12}^{(1)}, \vec{\alpha}_{12}^{(2)}, \vec{\alpha}_{12}^{(2)}$

on the final layer(prediction) they employed *averaging* to get back to $F'$ features.
![[Pasted image 20240912183654.png]]
## References

[Graph Attention Networks](https://arxiv.org/abs/1710.10903)
[video](https://www.youtube.com/watch?v=uFLeKkXWq2c) about the paper. 

[Graph Attention Networks Paper Explained With Illustration and PyTorch Implementation](https://epichka.com/blog/2023/gat-paper-explained/)
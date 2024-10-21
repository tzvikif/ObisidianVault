

2024-09-08 22:25

Status:

Tags: #paper, #video 

## GCNConv

if we look at the process as message passing:
$h_i=\displaystyle \sum_{j\in{N_i}}Wx_i$
the problem with that formula that the size of $h_i$ depends on the number of
its neighbors. to overcome that we normalize in the number of degree.
Aleksa says that it can lead to [[exploding_vanishing_gradient]]  gradient.

 $h_i=\frac{1}{\sqrt{deg(i)}\sqrt{deg(j)}}\displaystyle \sum_{j\in{N_i}}Wx_i$
in matrix notation:
$H^{(l+1)}=\sigma(\tilde{D}^{-\frac{1}{2}}\tilde{A}\tilde{D}^{-\frac{1}{2}}H^{(l)}W^{(l)})$

<u>1st perspective</u>\
Aleksa explain  briefly the how the author started from [[spectral graph convolution]] method and finished with the spacial convolution mention above.

<u>2nd perspective</u>
the paper claims that we can interpret out GCN model a differentiable and parameterized generalization of 1-dim [[Weisfiler_Lehman_algorithm]](are two graphs isomorphic?) algorithm on graphs.

<u>3nd perspective</u>
special case of [[GAT]] which the weights are constant.

<u>Experiment on Model Depth</u>

2-3 layers gave the best results.

## References


[Graph Convolutional Networks (GCN) | GNN Paper Explained](https://www.youtube.com/watch?v=VyIOfIglrUM)

[Semi-Supervised Classification with Graph Convolutional Networks](https://arxiv.org/abs/1609.02907)

further reading

[Graph Convolutional Networks (GCN) & Pooling](https://jonathan-hui.medium.com/graph-convolutional-networks-gcn-pooling-839184205692)


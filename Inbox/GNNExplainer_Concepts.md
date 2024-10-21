

2024-09-03 20:58

Status:

Tags:

## GNNExplainer_Concepts

capture the important input features by generating mask that will lead to the same prediction as the original GNN model.
learning **soft mask** on edges and features via optimization.
different masks are generated such as:
- node masks
- edge masks
- node feature masks
depending of the prediction task.

![[Pasted image 20240903210030.png]]

after the optimization , we have the masks.
those masks are combined with the input graph to obtain new graph via element-wise multiplication.
the new graph is fed into the trained GNN. using the score we evaluate it and update the masks.




## References

[[GNNExplainer]]
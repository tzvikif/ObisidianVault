

2024-09-10 23:42

Status: 

Tags: #video

## AUC

![[Pasted image 20240910234832.png|300]]


$TPR=\frac{TP}{TP+FN}$
$FPR=\frac{FP}{FP+TN}$

### intuitive explanation 
the yellow curve is the worst. because if i want to improve my TPR
i have to "pay" almost as much and gain FPR.
on the other hand with the blue curve. if i want to improve my TPR
(big step upwards) the TPR almost doesn't change(tiny move to the right)

### calculating the area under the graph
in practice we don't take all the point between [0, 1] in the boundary.
for instance we can take the values: $0.0, 0.2, 0.4,\ldots, 1.0$
and get:
![[Pasted image 20240911000603.png|300]]

more area under the curve $\Rightarrow$ better ROC


## References

[The ROC Curve : Data Science Concepts](https://www.youtube.com/watch?v=SHM_GgNI4fY&t=432s)
[ROC Curve and AUC Value](https://www.youtube.com/watch?v=QBVzZBsif20)

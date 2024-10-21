

2024-09-10 18:40

Status: 

Tags: #video

## The ROC Curve

there is a company **Statflix**
the company want to predict who is going to unsubscribe(churn)
in that case they can give him lower price or 1 month for free.
they trained a model M.
and tested it on test set and they got confusion matrix
predicted


![[Pasted image 20240910195510.png]]


$TPR=\frac{TP}{TP+FN}$
$FPR=\frac{FP}{FP+TN}$

![[Pasted image 20240910211829.png|300]]

above the line predict as leave(churn)

![[Pasted image 20240910211907.png|300]]
for more details:  [[ROC.excalidraw]]
if the boundary is at orange TPR will be  high FPR will be high (orange star)
if the boundary is at the blue line TPR will be low FPR will be low(blue start)

by moving the blue line a little bit to the left the TPR will increase significantly and the FPR will hardly change. that's why the red line is a curve and not linear.

to create the curve take the value from 0 to 100. practically move the line from 0 to 100. 
calculate the confusion matrix the TPR and the FPR. and draw a point.

### how to compare two ROC curves?

we use a metric which is called **A**rea **U**nder **C**urve [[AUC]] to evaluate the ROC.


## References

[The ROC Curve : Data Science Concepts](https://www.youtube.com/watch?v=SHM_GgNI4fY&t=432s)



2024-07-15 19:52

Status:

Tags: #paper

## Overview

- GNNExplainer identifies a subgraph which has the most impact predicting the labels.
- it uses [[model-agnostic]] approach
## Introduction
the virtue of understanding gnn predictions:
-  increase trust in GNN model. because we don't see it as a model that we don't have a clue how it works.
- better understanding of the network characteristics. and identify mistakes.
- recent approaches:
	- locally approximates models with simpler [[surrogate models]]
-  GNNExplainer specifies an explanation as rich subgraph. that subgraph maximizes the [[mutual information]] achieved by formulating a [[Mean Field Variational Approximation]] and learning *graph mask* which selects the importance subgraph for each [[computational graph]]
- GNNExplainer learns a *feature mask* that masks out unimportant node features. taking just a subset of features from a node.

![[Pasted image 20240716165411.png]]






## References

- [GNNExplainer paper](https://arxiv.org/pdf/1903.03894)
-  [[background on graph neural networks]]
- 

## questions
[[GNNExplainer questions]]

# Stat992 
## This blog brief introduces the technique of GCN.

# Introduction
This paper considers the problem of classifying nodes in a graph where only a small part of nodes have labels. The GCN introduced in this paper belongs to the family of spectral graph convolutional networks.

# Overview of this technique
<p align="center"><img width="50%" src="GCN.PNG" /></p>

On this figure, ![](https://latex.codecogs.com/svg.latex?X) is the original features of nodes (Some nodes have labels and some nodes don't have labels). ![](https://latex.codecogs.com/svg.latex?Z) is the final prediction of nodes and ![](https://latex.codecogs.com/svg.latex?Y) is the ground-truth label for nodes (Not all nodes have labels). ![](https://latex.codecogs.com/svg.latex?C) is the channel number of input layer and ![](https://latex.codecogs.com/svg.latex?F) is the channel number of output layer.

# Math Formula

![](https://latex.codecogs.com/svg.latex?X) is the matrix of node features vectors, ![](https://latex.codecogs.com/svg.latex?A) is the adjacency matrix and ![](https://latex.codecogs.com/svg.latex?D) is the degree metrix.

Let ![](https://latex.codecogs.com/svg.latex?\tilde{A}=A+I_{N}) which is the adjacency matrix with added self-connection. The paper uses the first order approximation of spectral decomposition to get a simple form of graph model (Please refer to the original paper for the detailed math derivation https://arxiv.org/pdf/1609.02907.pdf):

They calculate ![](https://latex.codecogs.com/svg.latex?\hat{A}=\tilde{D}^{-1/2}\tilde{A}\tilde{D}^{-1/2}) and the forward model for calculating the representation of nodes is 
![](https://latex.codecogs.com/svg.latex?Z=f(X,A)={\rm%20softmax}(\hat{A}{\rm%20ReLU}%20(\hat{A}XW^{(0)})W^{(1)})%20), 
where ![](https://latex.codecogs.com/svg.latex?W^{(0)}) is the input-to-hidden weight matrix and ![](https://latex.codecogs.com/svg.latex?W^{(1)}) is the hidden-to-output weight matrix and they are trained using gradient descent.

The loss is computed from cross-entropy from the labeled nodes in the graph:
![](https://latex.codecogs.com/svg.latex?{\rm%20Loss}=-\sum_{l%20\in%20{\rm%20labeled}}%20\sum_{f=1}^{F}%20Y_{lf}{\rm%20log}(Z_{lf}))


# One example:

### Dataset


|          Dataset        | Type  | Nodes  |  Edges | Classes | Features |  Label Rate|
| ---------------------- | ------------ | ------------ | ------------ | ------------ | ------------ | ------------ |
| Cora        | Citation Network | 2708 |  5429 | 7 | 1433 | 0.052  |

The citation links are the undirected edges and the sparse bag-of-words feature vectors of each document are the nodes.

### Experiments

The training log is shown here:
<p align="center"><img width="50%" src="training.PNG" /></p>
It could achieve a high accuracy with high speed.

# References

https://arxiv.org/pdf/1609.02907.pdf

https://github.com/tkipf/pygcn




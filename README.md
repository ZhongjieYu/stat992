# stat992
# blog post of a technique related to the graph.
# Introduction
This paper considers the problem of classifying nodes in a graph where only a small part of nodes have labels. The GCN introduced in this paper belongs to the family of spectral graph convolutional networks.

# 
![](https://latex.codecogs.com/svg.latex?X) is the matrix of node features vectors, ![](https://latex.codecogs.com/svg.latex?A) is the adjacency matrix and ![](https://latex.codecogs.com/svg.latex?D) is the degree metrix.

Let ![](https://latex.codecogs.com/svg.latex?\tilde{A}=A+I_{N}) which is the adjacency matrix with added self-connection. The paper uses the first order approximation of spectral decomposition to get a simple form of graph model:

They calculate ![](https://latex.codecogs.com/svg.latex?\hat{A}=\tilde{D}^{-1/2}\tilde{A}\tilde{D}^{-1/2}) and the forward model for calculating the representation of nodes is 
![](https://latex.codecogs.com/svg.latex?Z=f(X,A)={\rm%20softmax}(\hat{A}{\rm%20ReLU}%20(\hat{A}XW^{(0)})W^{(1)})%20) 


# 

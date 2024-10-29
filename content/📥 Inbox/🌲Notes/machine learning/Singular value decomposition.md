---
tags: ML/algo
aliases: SVD
---

# Singular value decomposition

## What does it do? 
Similar to PCA, it is a [[Dimentionality reduction]] [[Machine learning]]technique. It is done using matrices instead of transformation as in PCA.

## Math works
In SVD a matrix $A_{m\times n}$ is divided into 2 unitary matrices $U$ and $V$ which are [[orthogonal matrices]] and $\Sigma$, a rectangular diagonal matrix of singular values.
$$A_{m\times n}=U_{m\times m}\cdot\Sigma_{m\times n}\cdot\ {V^T_{n\times n}}$$
$A^T.A=(V.{\Sigma}^T.U^T)(U.\Sigma .V^T)=V.\Sigma^T.\Sigma .V^T$          [^1]  
$A.A^T=(U.\Sigma .V^T)(V.{\Sigma}^T.U^T)=U.\Sigma.\Sigma^T.U^T$          [^2]

Using SVD, we basically rotate(using U)->strech(using $\Sigma$)->rotate(using $V^T$)[^R1].

for an example with detailed math, check out [ref vid](https://www.youtube.com/watch?v=4tvw-1HI45s&ab_channel=RANJIRAJ). 
## Concepts used: 
Read up on these concepts for better understanding of this topic: 
Matrices->Cramer's rule
Graham Schmidt process for orthogonalisation

Footnotes: 
[^1]: From this equation, we get $V^T$ later in our decomposition.
[^2]: From this equation, we get U for the main SVD equation

## References
[^{R1}]:  [Ranji Raj YT video on SVD](https://www.youtube.com/watch?v=4tvw-1HI45s)

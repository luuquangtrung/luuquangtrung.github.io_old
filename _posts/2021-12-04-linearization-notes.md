---
title: "Some linearization techniques in linear programming"
date: 2021-12-04
permalink: /posts/2021/12/notes-linearization/ 
read_time: false
categories:
  - blog
<!-- header:
  teaser: /images/AI.jpg -->
tags:
  - linearization
  - linear program
---


## Product of two variables
A product term $x_ix_j$, where $x_i,x_j \in \{0,1\}$ occuring in a linear program can be replaced by an auxiliary continuous variable $y_{ij} \in [0,1]$ and the following so-called Fortet' constraints: [Fortet1960]:

$$
\begin{align*}
y_{ij}\leq & x_{i}\\
y_{ij}\leq & x_{j}\\
y_{ij}\geq & x_{i}+x_{j}-1
\end{align*}
$$

## References
[Fortet1960] R. Fortet. Applications de l’algèbre de Boole en recherche opérationelle. *Revue Française de Recherche Opérationelle*, 4:17–26, 1960.

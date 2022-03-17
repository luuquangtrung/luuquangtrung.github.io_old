---
title: "Some linearization techniques in linear programming"
layout: single
date: 2021-12-04
permalink: /posts/2021/12/notes-linearization/ 
read_time: false
categories:
  - blog
header:
  teaser: /files/post_materials/lp.png
tags:
  - linearization
  - linear program
---


Linear programming (LP) is the minimization of a linear form on a polyhedron[^Dantzig1955]. The standard form of an LP is

$$
\begin{align*}
\min & \quad c^\top x \\
     & \quad Ax = b, \\
     & \quad x \geq 0,
\end{align*}
$$

where $$c \in \mathbb{R}^n$$, $$b \in \mathbb{R}^m$$, and $$A$$ is the $$m{\times}n$$-matrix of coefficients. LP has been shown to be fell into the computational complexity class *P*[^Liberti2018]. It is hard sometimes to cast the problem as an LP. It such situation we may need to add some integer or binary variables. This leads us to an MILP (mixed integer LP) problem, which includes ILP (integer variables only), BLP (binary variables only), or LP as a special case. MILP is another fundamental problem in mathematical programming, and has been shown to be *NP*-hard[^Liberti2018].  


[^Dantzig1955]: [Dantzig1955] G. Dantzig, A. Orden, and P. Wolfe. The generalized simplex method for minimizing a linear form under linear inequality restraints. Pacific Journal of Mathematics, 5(2):183–196, 1955.

[^Liberti2018]: [Liberti2018] L. Liberti, Mathematical Programming. *Lecture Notes*, Ecole Polytechnique, 2018.


## Some linearization techniques
Following are some linearization techniques which transform nonlinear terms to linear forms, which may involve additional (usually integer or binary) variables.

##### Rounding functions: Ceil and Floor

A floor function $$y = \lfloor x \rfloor$$ can be linearized as[^SE_round]


$$
\begin{align*}
& x - 0.999 \leq y \leq x, \\
& y \in \mathbb{Z_+}. 
\end{align*}
$$

Similarly, a ceiling function $$y = \lceil x \rceil$$ can be linearized as

$$
\begin{align*}
& x \leq y \leq x + 0.999, \\
& y \in \mathbb{Z_+}. 
\end{align*}
$$

[^SE_round]: StackExchange, [*Linear program with ceiling or floor functions*](https://math.stackexchange.com/questions/1862885/linear-program-with-ceiling-or-floor-functions). Accessed Feb. 2022.


##### Product of two binary variables
A product term $$xy$$, where $$x,y \in \{0,1\}$$ occuring in a linear program can be replaced by an auxiliary continuous variable $$z \in [0,1]$$ and the following so-called Fortet' constraints[^Fortet1960]:

$$
\begin{align*}
z & \leq x, \\
z & \leq y, \\
z & \geq x + y - 1.
\end{align*}
$$

[^Fortet1960]: [Fortet1960] R. Fortet. Applications de l’algèbre de Boole en recherche opérationelle. *Revue Française de Recherche Opérationelle*, 4:17–26, 1960.


##### Product of multiple binary variables
The above technique could also be extended to the product of multiple variables: $$z_\mathcal{I} = \prod_{i \in \mathcal{I}} x_i$$, where $$x_i \in \{0,1\}$$, $$\forall i \in \mathcal{I}$$. The linearization constraints are[^2]

$$
\begin{align*}
z_{\mathcal{I}} & \leq x_{i}, \quad \forall i \in \mathcal{I}, \\
z_{\mathcal{I}} & \geq \sum_{i \in \mathcal{I}} x_{i} - |\mathcal{I}| + 1.
\end{align*}
$$

##### Product of a binary and a non-negative continuous variable

Suppose we have a binary variable $$x \in \{0,1\}$$ and a non-negative continuous variable $$y \in \mathbb{R_+}$$. The product $$z = xy$$ is thus

$$
z=\begin{cases}
0 & \text{if }x=0, \\
y & \text{if }x=1.
\end{cases}
$$

$$z$$ can be linearized by using the so-called big-$$M$$ method[^SE_prod],

$$
z \geq y - (1-x)M,
$$

where $$z \in \mathbb{R_+}$$ is a continuous variable, $$M$$ is a sufficiently large value so that it would not be part of any feasible solution.



[^SE_prod]: : StackExchange, [*How to linearize the product of a binary and a non-negative continuous variable?*](https://or.stackexchange.com/questions/39/how-to-linearize-the-product-of-a-binary-and-a-non-negative-continuous-variable). Accessed Feb. 2022.

### References


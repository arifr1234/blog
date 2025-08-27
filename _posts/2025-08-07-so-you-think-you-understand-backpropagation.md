---
layout: post
title: So you think you understand backpropagation?
---
# Backpropagation - the misunderstood implementation detail with good press


# Intro
In this blog post I'll explain the interesting maths behind the widely misunderstood term "backpropagation" in the context of deep learning.

It has always baffled me how few good math explainers are there for backpropagation, especially considering how common this term is in the deep learning discourse.

Steven Johnson's lecture "So You Think You Know How to Take Derivatives?", contains a 3 minutes section that is the best explanation I have ever heard for backpropagation, and this blog post is my attempt to adapt this explanation to a more wide audience.
## Required prior knowledge
I'll assume some basic knowledge in linear algebra, and expect you to know what a derivative is, but won't assume any prior knowledge in the field of deep learning.

While backpropagation has a formal definition, it is very common to confuse it with the whole deep learning training process. As a result, the first section is dedicated for definitions.

# Background
We first need to understand some terms.
## Optimization is intelligence
Let's start with a problem.









One of the most common ways to achieve an "intelligent" solution to a problem, is to view that problem as an optimization problem.
There has been expensive research of 




To get to backpropagation we first need to understand deep learning.

Deep learning, just like many other "intelligent" algorithms, relies on *optimization*.

and to understand deep learning we first need to understand its' backbone: continuous optimization.
## Continuous optimization
Continuous optimization deels with solving problems that look like this finding:
$$
\arg\min_\theta L(\theta)
$$
For some function $L(\theta)$.

Which means finding the value of some variable (the symbol in the subscript) that corresponds to the smallest value of the expression.

For example:
$$\arg\min_x 1+(x-5)^2 = 5$$
$$\min_x 1+(x-5)^2 = 1$$
A real life example using $\max$ this time:
$$
\max_c H(c) = 8,848.86\ \text{meters}
$$
$$
\arg\max_c H(c) = 
\begin{bmatrix}
27.988333 \\ 86.925278
\end{bmatrix}
$$
Where $H(c)$ is a function that accepts a coordinate ($\begin{bmatrix}latitude \\ longitude\end{bmatrix}$) on earth and outputs the hight above sea level at that coordinate.
We get the hight and coordinates of Mount Everest, respectively.

Notice how $\arg\max$ is defined also when the argument is a vector.

How is it that such a simple problem leads to so 
---
layout: post
title: L-Lipschitz Continuity and Lipschitz Condition
date: 2020-03-26
Author: Yihan
categories: [note]
tags: [Real Analysis]
comments: true
---

Hope this note can recall some of real analysis.

Download `pdf` here: [Not available yet]

### 1. General Definition of Lipschitz continuous

#### 1.1 Lipschitz Function

A function $f$ satisfies:
$$
|f(x)-f(y)|\leq M|x-y|
$$
is called a **Lipschitz Function**.

#### 1.2 Lipschitz Condition

A function $f$ defined on a subset $E$ of $R^d$ satisfies a **Lipschitz condition** on $E$ if there exists $M>0$ such that 
$$
|f(x)-f(y)|\leq M|x-y|
$$
for all $x,y \in E$.

More generally, a function $f$ satisfies a **Lipschitz condition with exponent $\gamma$** (or is $H\ddot{o}lder$ $\gamma$ ) if 
$$
|f(x)-f(y)|\leq M|x-y|^\gamma
$$
for all $x,y \in E$.

#### 1.3 An Interesting Proposition

Here is an interesting proposition: 

Let $f: R\rightarrow R$. $f$ satisfies Lipschitz condition 
$$
|f(x)-f(y)|\leq M|x-y|
$$
for some $M$ and all $x,y \in R$, iff $f$ satisfies the following two properties:

- $f$ is absolutely continuous
- $|f'(x) \leq M|$ for $a.e.$  $x$.

This is an exercise in Stein's Real Analysis. This proposition indicates that Lipschitz continuous is more strict than common continuous. If $f$ satisfies a Lipschitz condition, then it's absolutely continuous, and its first-order derivative is bounded. This means that Lipschitz continuity have better properties than common continuity.

*Proof:*

Suppose that $f$ is Lipschitz, we use $\delta-Lipschitz$. For any $\epsilon > 0$,  let $\delta = \frac{\epsilon}{M}$, thus
$$
\sum|b_j-a_j|<\delta\rightarrow \sum|f(b_j)-f(a_j)|< \epsilon
$$
So, $f$ is absolutely continuous. 

Suppose $x_0$ is a point for which $f'(x)$ exists, the Lipschitz condition implies $|\frac{f(x+h)-f(x)}{(x+h)-x}|\leq M$ for all $h$. Taking the limit as $h\rightarrow 0$:
$$
\lim_{h\rightarrow 0}|\frac{f(x+h)-f(x)}{h}|\leq M \Rightarrow |f'(x)|\leq M
$$
**Conversely**, suppose $f$ is absolutely continuous and has bounded derivative. Since ==absolutely continuous functions are the integrals of their derivatives==,
$$
|f(y)-f(x)| = |\int_x^yf'(t)dt|\leq \int_{min(x,y)}^{max(x,y)}|f'(t)dt|\leq \int_{min(x,y)}^{max(x,y)}Mdt = M|x-y|
$$
So, $f$ is Lipschitz.

### 2.  Lipschitz Continuous Gradient

#### 2.1 Properties

If $\nabla f(x)$ is L-Lipschitz continuous, then we have

- $||\nabla f(x)-\nabla f(y)||\leq L||x-y||$

- $\frac{L}{2}x^Tx - f(x)$ is convex(when the domain of $f$, denoted as $dom(f)$ is convex)
- $\nabla^2f(x)\leq L·I$(if $f(x)$ is twice differentiable)
- $f(y)\leq f(x)+\nabla f(x)(y-x) + \frac{L}{2}||y-x||^2$(if $f(x)$ is convex)




---
date: 2020-12-31T14:04
tags:
  - mathematics
  - category theory
---

# Anamorphism

In functional programming, an anamorphism is a generalization of the concept of [[[56e94cd9]]]. Formally, anamorphisms are generic functions that can corecursively construct a result of a certain type and which is parameterized by functions that determine the next single step of the construction.

The categorical dual of the anamorphism is the [[[d1b1f980]]].


$$\begin{CD}
F A @>{F h}>> F B\\
@A{f}AA @A{g}AA \\
A @>{h}>> B
\end{CD}$$

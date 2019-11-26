---
layout: page
title: 7. Moving Beyond Linearity
---

{% katexmm %}

# Conceptual Exercises

<div class="toc"><ul class="toc-item"><li><span><a href="#exercise-1-the-truncated-power-basis-generates-cubic-regression-splines" data-toc-modified-id="Exercise-1:-The-truncated-power-basis-generates-cubic-regression-splines-1">Exercise 1: The truncated power basis generates cubic regression splines</a></span><ul class="toc-item"><li><span><a href="#a" data-toc-modified-id="a.-1.1">a.</a></span></li><li><span><a href="#b" data-toc-modified-id="b.-1.2">b.</a></span></li><li><span><a href="#c" data-toc-modified-id="c.-1.3">c.</a></span></li><li><span><a href="#d" data-toc-modified-id="d.-1.4">d.</a></span></li><li><span><a href="#e" data-toc-modified-id="e.-1.5">e.</a></span></li></ul></li><li><span><a href="#exercise-2-alternative-roughness-penalties-for-smoothing-splines" data-toc-modified-id="Exercise-2:-Alternative-roughness-penalties-for-smoothing-splines-2">Exercise 2: Alternative roughness penalties for smoothing splines</a></span><ul class="toc-item"><li><span><a href="#a" data-toc-modified-id="a.-2.1">a.</a></span></li><li><span><a href="#b" data-toc-modified-id="b.-2.2">b.</a></span></li><li><span><a href="#c" data-toc-modified-id="c.-2.3">c.</a></span></li><li><span><a href="#d" data-toc-modified-id="d.-2.4">d.</a></span></li><li><span><a href="#e" data-toc-modified-id="e.-2.5">e.</a></span></li></ul></li><li><span><a href="#exercise-3-example-basis-function-model" data-toc-modified-id="Exercise-3:-Example-basis-function-model-3">Exercise 3: Example basis function model</a></span></li><li><span><a href="#exercise-4-example-basis-function-model" data-toc-modified-id="Exercise-4:-Example-basis-function-model-4">Exercise 4: Example basis function model</a></span></li><li><span><a href="#exercise-5-comparing-smoothing-splines-with-different-roughness-penalties" data-toc-modified-id="Exercise-5:-Comparing-smoothing-splines-with-different-roughness-penalties-5">Exercise 5: Comparing smoothing splines with different roughness penalties</a></span><ul class="toc-item"><li><span><a href="#a" data-toc-modified-id="a.-5.1">a.</a></span></li><li><span><a href="#b" data-toc-modified-id="b.-5.2">b.</a></span></li><li><span><a href="#c" data-toc-modified-id="c.-5.3">c.</a></span></li></ul></li></ul></div>

## Exercise 1: The truncated power basis generates cubic regression splines

### a.

If $x \leqslant \xi$ then $(x-\xi)_+^3 = 0$. So if we take $a=1 = \beta_0, b_1 = \beta_1, c_1 = \beta_2, d_1 = \beta_3$, then $f(x) = f_1(x)$ for all $x \leqslant \xi$

### b. 

If $x > \xi$ then $(x-\xi)_+^3 = (x-\xi)^3$. Then expanding $f(x)$

$$f(x) = (\beta_0 - \beta_4 \xi^3) + (\beta_1 + 3\beta_4\xi^2)x + (\beta_2 - 3\beta_4\xi)x^2 + (\beta_3 + \beta_4)x^3$$

we see 

\begin{align}
a_1 &= \beta_0 - \beta_4 \xi^3\\
b_1 &= \beta_1 + 3\beta_4\xi^2\\
c_1 &= \beta_2 - 3\beta_4\xi\\
d_1 &= \beta_3 + \beta_4
\end{align}

### c.

\begin{align}
f_2(\xi) &= (\beta_0 - \beta_4 \xi^3) + (\beta_1 + 3\beta_4\xi^2)\xi + (\beta_2 - 3\beta_4\xi)\xi^2 + (\beta_3 + \beta_4)\xi^3\\
&= \beta_0 - \beta_4\xi^3 +\beta_1\xi + 3\beta_4\xi^3 + \beta_2\xi^2 - 3\beta_4\xi^3 + \beta_3\xi^3 + \beta_4\xi^3\\
&= \beta_0 + \beta_1\xi + \beta_2\xi^2 + \beta_3\xi^3\\
&= f_1(\xi)
\end{align}

### d. 

\begin{align}
f'_2(\xi) &=  (\beta_1 + 3\beta_4\xi^2) + 2(\beta_2 - 3\beta_4\xi)\xi + 3(\beta_3 + \beta_4)\xi^2\\
&= \beta_1 + 3\beta_4\xi^2 + 2\beta_2\xi - 6\beta_4\xi^2 + 3\beta_3\xi^2 + 3\beta_4\xi^2\\
&= \beta_1 + 2\beta_2\xi + 3\beta_3\xi^2\\
&= f'_1(\xi)
\end{align}

### e.

\begin{align}
f''_2(\xi) &= 2(\beta_2 - 3\beta_4\xi) + 6(\beta_3 + \beta_4)\xi\\
&= 2\beta_2 + 6\beta_4\xi\\
&= f''_1(\xi)
\end{align}

## Exercise 2: Alternative roughness penalties for smoothing splines

We're just going to describe the solutions instead of drawing them.

### a.

If $\lambda = \infty$ and $m = 0$, then the integral term is minimized by a zero integral, hence by $g^{(0)} = g = 0$. So $\hat{g}$ is the zero function.

### b.

In this case, the integral is minimized by $g' = 0$, so $\hat{g}$ is a constant function. Likely $g = \beta_0 = \overline{y}$

### c.

This is the smoothing spline discussed in the chapter -- $\hat{g}$ is the ordinary least squares line.

### d. 

Now the integral penalty forces $g^{(3)} = 0$, so $g$ is necessarily polynomial of degree leqslant 2. It's clear that it necessarily has degree 2 -- one can imagine cases where a linear $\hat{g}$ minimizes the RSS term, and cases where a quadratic does. In general, a quadratic has more freedom, so averaging over datasets, the quadratic will have smaller RSS, and hence $\hat{g}$ will be quadratic.

### e.

In this case, the $m = 3$ condition is irrelevant. Now we are minimizing the RSS over *all* functions $g$, so $\hat{g}$ will be any function which has zero RSS (i.e. which has $\hat{g}(x_i) = y_i$ for all $i$). For example, the interpolation spline, or a step (piecewise constant) function which passes through the y_i will have zero RSS. Such a function isn't unique.

### Exercise 3: Example basis function model

skip

### Exercise 4: Example basis function model

skip

### Exercise 5: Comparing smoothing splines with different roughness penalties

### a. 

As $\lambda \rightarrow \infty$, the integral much approach 0. Then $\hat{g}_1$ approaches a polynomial of degree at most 2, and $\hat{g}_2$ approaches a polynomial of degree 3. Since $\text{deg}(\hat{g}_1) \leqslant \text{deg}(\hat{g}_2)$, we expect $\text{RSS}_{train}(\hat{g}_1) \geqslant \text{RSS}_{train}(\hat{g}_2)$

### b.

Since $\text{deg}(\hat{g}_1) \leqslant \text{deg}(\hat{g}_2)$, we expect $\text{RSS}_{test}(\hat{g}_1) \leqslant \text{RSS}_{test}(\hat{g}_2)$

### c.

For $\lambda = 0$, the roughness penalty vanishes and both $\hat{g}_1, \hat{g}^2$ can be any function with zero RSS (see [Exercise 2 e.](#Exercise-2:-Alternative-roughness-penalties-for-smoothing-splines) above). Such functions aren't uniquely defined, so in the absence of a rule for choosing $\hat{g}_1, \hat{g}_2$ in this case, we can't answer the question.

{% endkatexmm %}
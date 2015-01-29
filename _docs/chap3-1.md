---
layout: docs
title: Asymptotic notation
permalink: /docs/chap3-1/
---
###Solution 3.1-1
Let's call $$h(n) = \max (f(n), g(n))$$, i.e.,
\\[
h(n) = 
    \\begin{cases}
        f(n)  & \mbox{when }  f(n) \geq g(n) \\\\\\
        g(n) & \mbox{otherwise}
    \\end{cases}
\\]
If we are able to find $c\_1$, $c\_2$ and $n\_0$ which satisfies following equation, 
we have $\max (f(n), g(n)) = \Theta(f(n) + g(n))$.
\\begin{align\*}
0 \\leq c\_1 (f(n) + g(n)) \\leq h(n) \\leq c\_2 (f(n) + g(n)) && \\text{for some } n \\geq n\_0
\\end{align\*}
Assume $f(n) \geq g(n)$, and take $c\_1 = 1/2$ and $c\_2 = 2$,
\begin{align\*}
0 \leq \frac{1}{2} (f(n) + g(n)) \leq f(n) \leq 2 (f(n) + g(n)) && \text{holds for } n \geq n\_0 \text{ where } n\_0 = \max (n\_f, n\_g)
\end{align\*}
Similary, with the same constants the equality holds when $f(n) < g(n)$. Hence, $\max (f(n), g(n)) = \Theta(f(n) + g(n))$.

###Solution 3.1-2
\\[
(n + a)^b = {n \\choose 0} n^b + {n \\choose 1} n^{b-1} a + \\ldots + {n \\choose n} a^n 
\\]

\\[
(n + a)^b  \\geq {n \\choose 0} n^b 
\\]
i.e.,
\\[
(n + a)^b = \\Omega(n^b) 
\\]
where $c\_1 = 1$ and $n\_0 = 1$.

Also,
\\[
(n + a)^b  \\leq {n \\choose 0} n^b + {n \\choose 1} n^b + \\ldots + {n \\choose n} n^b
\\]
i.e.,
\\[
(n + a)^b = O(n^b) 
\\]
where $c\_2 = \sum\_{i = 0}^{n} {n \choose i}$ and $n\_0 = 1$.
Hence, $(n + a)^b = \Theta(n^b) $.

### Solution 3.1-3
The $O$-notation provides an upper bound. "At least" implies a lower bound.

### Solution 3.1-4
The following inequality should hold for $2^{n+1} = O(2^n)$

\\[
0 \\leq 2^{n+1} \\leq c \\cdot 2^n \\hspace{1cm} \\text{ for some } n \\geq n\_0
\\]
This holds for $c = 2$ and $n\_0 = 1$. Hence, $2^{n+1} = O(2^n)$.

\\[
0 \\leq 2^{2n} \\leq c \\cdot 2^n 
\\]
does not hold as $c = 2^n$ if this has to hold. But, $c$ should be a constant.

### Solution 3.1-5
Given, $f(n) = \\Omega(g(n))$ and $f(n) = O(g(n))$. So,
\\begin{align\*}
0 \\leq c\_1 g(n) \\leq f(n) && \\mbox{for } n \\geq n\_1 \\\\
0 \\leq f(n) \\leq c\_2 g(n) && \\mbox{for } n \\geq n\_2
\\end{align\*}
From these, we have,
\\begin{align\*}
0 \\leq c\_1 g(n) \\leq f(n) \\leq c\_2 g(n) && \\mbox{for } n \\geq \\max (n\_1, n\_2)
\\end{align\*}
Or, $f(n) = \\Theta(g(n))$. 

### Solution 3.1-6
This is the verbal statement of Exercise {3.1-5}.

### Solution 3.1-7
Assume, $f(n) = o(g(n))$ and $f(n) = \omega(g(n))$. From the first definition, we have
\\[
  \lim\_{n \rightarrow \infty} \dfrac{f(n)}{g(n)} = 0
\\]
Hence, $\lim\_{n \rightarrow \infty} \dfrac{f(n)}{g(n)} \ne \infty$.

Or, $f(n) \\ne \\omega(g(n))$. We have a contradiction. And there is no $f(n)$ such that $f(n) = o(g(n))$ and $f(n) = \\omega(g(n))$.

### Solution 3.1-8
\\[
\\Omega(g(n,m)) =
    \\begin{cases}
 		f(n,m): \\mbox{there exist positive constants } c,n\_0 \\mbox{ and } m\_0 \\mbox{ such that } \\\\\\
 		 0 \\leq c g(n,m) \\leq f(n,m) \\mbox{ for all } n \\geq n\_0 \\mbox{ or }  m \\geq m0.
	\\end{cases}
\\]

\\[
\\Theta(g(n,m)) = 
    \\begin{cases}
 		f(n,m): \\mbox{there exist positive constants } c\_1, c\_2, n\_0 \\mbox{ and } m\_0 \\mbox{ such that } \\\\\\
 		 0 \\leq c\_1 g(n,m) \\leq f(n,m) \\leq c\_2 g(n,m) \\mbox{ for all } n \\geq n\_0 \\mbox{ or }  m \\geq m0.
	\\end{cases}
\\]


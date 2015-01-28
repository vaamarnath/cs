---
layout: default
title: Randomized algorithms
categories: clrs
---
### Solution 5.3-1
Pull iteration for $i = 1$ out of the loop, and then we satisfy the requirement
for new loop invariant condition. Now, just prior to the iteration of
**for** loop for each value of $ i = 2, 3,\ldots,n$, for each possible $(i -1) $ 
permutation, the subarray $A[1\ldots i - 1]$ contains this $(i - 1)$
permutation with probability $(n - i +1 )! / n!$.

The maintenance and termination parts of the algorithm remains the same. The
initialization part is for the subarray $A[1\ldots 1]$, which contains any 1
permutation with probability $(n - 1)!/n! = 1/n$.

### Solution 5.3-2
Although PERMUTE-WITHOUT-IDENTITY will not produce the identity permutation,
there are other permutations that it fails to produce. For example, consider
its operation when $n = 3$, when it should be able to produce the $n! - 1 = 5$
non-identity permutations. The for loop iterates for $i = 1$ and $i = 2$.
When $i = 1$, the call to RANDOM returns one of two possible values (either 2 
or 3), and when $i = 2$, the call to RANDOM returns just one value (3). Thus,
there are only $2 \cdot 1 = 2 $ possible permutations that
PERMUTE-WITHOUT-IDENTITY can produce, rather than the 5 that are required.

### Solution 5.3-3
The algorithm starts with given permutation of $n$ numbers. Consider the first
iteration of the loop, the first element is randomly swapped to one of the 
$1 \cdot n$ positions. After the first iteration, the given input permutation 
can end up in $n$ different permutations with equal probability of $\frac{1}{n}$. 
For each of the $n$ permutations, the second element gets randomly swapped with
one of the $n$ possiblities. After second iteration, there are $n^2$ possible
permutations of equal probability $\frac{1}{n^2}$. The loop is iterated $n$ 
times and this would result in $n^n$ possible permutations with equal probability
of $\frac{1}{n^n}$. Note that, each of the $n^n$ permutations are not unique
as have only $n!$ unique permutations.

If the algorithm is producing uniforming random permutations, each permutation
should be equally likely with probability $\frac{1}{n!}$. That is, each of the
repeated permutation should be equally repeated. In other words, all permutations 
should be produced $x$ times by the algorithm. Or,

\\begin{align}
\frac{x}{n^n} &= \frac{1}{n!} \\\\\\
x &= \frac{n^n}{n!} \\\\\\
&= \frac{n^{n - 1}}{(n - 1)!}
\\end{align}

$(n-1)! \nmid  n^{n - 1}$ for $n \geq 3$ and hence the algorithm can't produce
all $n!$ permutations with equal probability. 

### Solution 5.3-4

The algorithm PERMUTE-BY-CYCLES chooses a *offset* randomly in the range $[1, n]$ 
and then performs a cyclic rotation of the input permutation. Thus, the algorithm
can only produce any cyclic rotated version of the input permutation. The algorithm 
is capable of producing only $n$ permutation with probability of $1/n$ (the offset
is chosen with probability $1/n$) and all the rest $n! - n$ permutations have a
probability of 0. Therefore, the algorithm is unable to produce uniform random permutation.

### Solution 5.3-5
The algorithm PERMUTE-BY-SORTING using random number generator of range $[0, n^3 - 1]$.
The first number is chosen uniquely with probability 1. The second number is chosen 
uniquely with probability $\frac{n^3 - 1}{n^3}$. The third number is chosen uniquely 
with probability $\frac{n^3 - 2}{n^3}$. The probability that each number is chosen 
uniquely is,

\\begin{align}
P &= 1 \cdot \bigg(\frac{n^3 - 1}{n^3}\bigg) \cdot \bigg(\frac{n^3 - 2}{n^3}\bigg) \ldots \bigg(\frac{n^3 - n + 1}{n^3}\bigg) \\\\\\
&= 1 \cdot \bigg(1 - \frac{1}{n^3}\bigg) \cdot \bigg(1 - \frac{2}{n^3}\bigg) \ldots \bigg(1 - \frac{n + 1}{n^3}\bigg) \\\\\\
&\geq \bigg(1 - \frac{n}{n^3}\bigg) \cdot \bigg(1 - \frac{n}{n^3}\bigg) \ldots \bigg(1 - \frac{n}{n^3}\bigg) \\\\\\
&\geq \bigg(1 - \frac{1}{n^2}\bigg)^n \\\\\\
&\geq \bigg(1 - \frac{1}{n}\bigg) & \text{as } (1- x)^n \geq (1 - nx)
\\end{align} 

### Solution 5.3-6
Retry the algorithm till we get the unique elements as per requirement.

### Solution 5.3-7
Each combination have a probability of $\dfrac{1}{\{n \choose m\}}$. To prove, 
let's induct on $m$. 

**Base case:** For $m = 1 (\text{or } 0)$, the result is trivially true. 

**Inductive hypothesis:** Assume that this invariant holds good for $m - 1$.
The probability for choosing $m - 1$ elements from $n - 1$ choices is 
$^1/\_{n - 1 \choose m - 1}$. 

**Induction step:** Now to select $m$ elements from $n$ choices, we have two cases. 

Case 1: $n$ is included in the $m$ selected elements. This occurs when we have an
$i$ already in $m - 1$ selections or $n$ is $i$. We have $m$ way in which $n$ ends 
up in our final $m$ elements. 
Prob\{selecting $m$ elements randomly from $n$ elements\}, $P\_{m,n}$
\\begin{align}
P\_{m,n} &= \frac{m}{n} \cdot \frac{1}{\{n - 1 \choose m - 1\}} \\\\\\
& = \frac{m}{n} \cdot \frac{(m - 1)! (n - 1 - m + 1)!}{(n - 1)!} \\\\\\
& = \frac{m! (n - m)!}{n!} \\\\\\
& = \frac{1}{\{n \choose m\}}
\\end{align}

Case 2: $n$ is not included in the $m$ selected elements. This occurs when the last 
selected element is not in any of the $n - m$ already picked elements. 
Prob.\{selecting $m$ elements randomly from $n$ elements\}, $P\_{m,n}$
\\begin{align}
P\_{m,n} &= \frac{(n - m)}{n} \cdot P\_{m,n-1} \\\\\\
P\_{m,n} &= \frac{n - m}{n} \cdot \frac{1}{\{n - 1 \choose m\}}
\\end{align}

Now, let's prove $P\_{m,n-1} = 1/{n - 1 \choose m}$. By induction hypothesis,
we have $P\_{m - 1,n-1} = 1/{n - 1 \choose m - 1}$. 

\\begin{align}
P\_{m,n - 1} &= \frac{1}{\{n - 1 \choose m - 1\}}  \cdot \frac{1}{n - m} \cdot m \\\\\\
& = \frac{(m - 1)! (n - 1 - m + 1)!}{(n - 1)!} \cdot \frac{m}{n - m} \\\\\\
& = \frac{m! (n - m - 1)!}{(n - 1)!} \\\\\\
& = \frac{1}{\{n - 1 \choose m\}} \\\\\\
\implies P\_{m,n} &= \frac{n - m}{n} \cdot \frac{1}{\{n - 1 \choose m\}} \\\\\\
&= \frac{n - m}{n} \cdot \frac{m! (n - m - 1)!}{(n - 1)!} \\\\\\
&= \frac{m!(n - m)!}{n!}  \\\\\\
&= \frac{1}{\{n \choose m\}}
\\end{align}
Hence, we have proved that the probability holds good for any $m, n$. 

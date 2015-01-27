---
layout: default
title: Indicator Random Variables
categories: clrs
---

### Solution 5.2-1
The best case, when only one hiring is done when the first candidate in the
interview queue is of the best rank. Anyone appearing after the candidate 1 is
not hired as they aren't better than him/her. Probability of this event is $
\frac{(n - 1)!}{n!} = \frac{1}{n} $.

The worst case scenario, where the $ n $ hiring is performed is when the
candidates are in increasing order of there skill set. For any $ i $, $ A[i] $
is better than any of the $ A[j] $ where $ j < i $. Probability of this event is
$ \frac{1}{n!} $.

### Solution 5.2-2
If the hiring occurs exactly two times, the best candidate should not appear as
the first candidate and all candidates appearing after the first should have
lower rank than him/her. In such a scenario, where the first candidate with rank
$ i $, ($ i < n $), all candidates with ranks $ i + 1, i + 2,..., n - 1 $ must
be interviewed after the best candidate with rank $ n $. 

Let, $ E\_{i} $ be the event that candidate $ 1 $ has rank  $ i $. Prob\{$ E\_i
$\} = $ \frac{1}{n} $ for any value of $ i $. Let $ j $ be the position of the
best candidate and $ F $ be the event in which candidates $ 2, 3,\ldots, j - 1 $
have ranks strictly less than rank of candidate 1. Given that event $ E\_i $ has
occurred, event $ F $ occurs when the $i$th ranked candidate is the first one
interviewed out of the $ n - i $ candidates.
Thus, Prob\{$ F | E\_i $\} = $ \frac{1}{n-i} $. 

The event A that the algorithm hires exactly twice is, (note $ E\_1, E\_2,\ldots, E\_n
$ are disjoint). 
\\begin{align\*}
 A =& F \cap (E\_1 \cup E\_2 \cup \ldots \cup E\_{n-1})  \\\\\\
 =& (F \cap E\_1) \cup (F \cap E\_2) \cup \ldots \cup (F \cap E\_{n-1})
\\end{align\*}
And,
\\begin{align\*}
 Prob\\{A\\} &=& \sum\_{i = 1}^{n - 1} Prob\{F \cap E\_i \}  
\\end{align\*}

We know, 
\\begin{align\*}
Prob\\{F \cap E\_i\\} =& Prob\\{F | E\_i\\} Prob\{E\_i\}  \\\\\\
=& \frac{1}{n - i} \cdot \frac{1}{n} 
\\end{align\*}

Therefore,
\\begin{align\*}
Prob\\{A\\} =& \sum\_{i = 1}^{n - 1} \frac{1}{n - i} \cdot \frac{1}{n}  \\\\\\
=& \frac{1}{n} \sum\_{i = 1}^{n - 1} \frac{1}{n - i}  \\\\\\
=& \frac{1}{n} \bigg(\frac{1}{n - 1} + \frac{1}{n - 2} + \ldots + \frac{1}{1}
\bigg) \nonumber \\\\\\
=& \frac{1}{n} \cdot \big( \ln(n) + O(1) \big) 
\\end{align\*}

### Solution 5.2-3
Let the following indicator variables denote the outcomes of a single dice,
\\[
I\_1  =  
\begin{cases}
1, & 1 \text{ if the dice rolls 1} \\\\\\
0, & \text{otherwise}
\end{cases}
\\]
\\[
I\_2  =  
\begin{cases}
1, & 1 \text{ if the dice rolls 2} \\\\\\
0, & \text{otherwise}
\end{cases}
\\]                    
\\[
I\_3  =  
\begin{cases}
1, & 1 \text{ if the dice rolls 3} \\\\\\
0, & \text{otherwise}
\end{cases}
\\]
\\[
I\_4  =  
\begin{cases}
1, & 1 \text{ if the dice rolls 4} \\\\\\
0, & \text{otherwise}
\end{cases}
\\]
\\[
I\_5  =  
\begin{cases}
1, & 1 \text{ if the dice rolls 5} \\\\\\
0, & \text{otherwise}
\end{cases}
\\]
\\[
I\_6  =  
\begin{cases}
1, & 1 \text{ if the dice rolls 6} \\\\\\
0, & \text{otherwise}
\end{cases}
\\]

Each indicator variable has probability of succeeding of $ \frac{1}{6} $. The
values rolled by $ n $ dice can be represented using $ n $ random variables $
X\_1, X\_2,..., X\_n $. And the sum of these random variables represents the sum
obtained by rolling the $ n $ dice. Expected value of $ X\_i $ is,
\\begin{align}
E[X\_i] &= \sum_{x = 1}^{6}  x \cdot P(x)  \\\\\\
&= 1 \cdot \frac{1}{6} + 2 \cdot \frac{1}{6} + 3 \cdot \frac{1}{6} + 4 \cdot \frac{1}{6} + 5 \cdot \frac{1}{6} + 6 \cdot \frac{1}{6}  \\\\\\
&= \frac{21}{6} \\\\\\
&= \frac{7}{2} 
\\end{align}

Expected value of $ X $ is,
\\begin{align}
E[X] &= E\bigg[\sum\_{i = 1}^{n}X\_i\bigg]   \\\\\\
&= \sum\_{i = 1}^{n} \bigg(E[X\_i]\bigg)  & \text{(by linearity of expectation)} 
\\\\\\
&= \sum\_{i = 1}^{n} \frac{7}{2}  \\\\\\
&= \frac{7}{2}n 
\\end{align} 

### Solution 5.2-4
Let's define the following indicator random variable,
\\[
I\_{i} = 
\begin{cases}
1, & \text{if } i\text{th customer got his/her hat back} \\\\\\
0, & \text{otherwise}
\end{cases}
\\]
The probability of $i$th customer getting his/her hat is $\frac{1}{n}$. And let
$E\_i$ denote the event where $i$th customer got his/her hat back. Then, we have,
\\begin{align}
E[X\_i] &= 1 \cdot \frac{1}{n} + 0 \cdot \frac{n - 1}{n} \\\\\\
&= \frac{1}{n} \\\\\\
\text{Now,}
E[X] &= E\bigg[\sum\_{i = 1}^{n} X\_i\bigg] \\\\\\
&= \sum\_{i = 1}^{n} E\bigg[X\_i\bigg] & \text{(by linearity of expectation)} \\\\\\
&= \sum\_{i = 1}^{n} \frac{1}{n} \\\\\\
&= n \cdot \frac{1}{n} \\\\\\
&= 1 
\\end{align} 

### Solution 5.2-5
Let's define the following indicator random variable,
\\begin{align}
I\_{ij} =
\begin{cases}
1, & \text{if } A[i] > A[j] \text{ with } 0 \leq i < j \leq n\\
0, & \text{otherwise}
\end{cases} \\
\\end{align}
Now,
\\begin{align}
Prob\\{I\_{ij} = 1\\} = \frac{1}{2} & \text{ as probability of } A[i] > A[j]\text{
is } \frac{1}{2}
\\end{align}
Let $X$ be the random variable denoting number of inverting pairs in the array,
\\begin{align}
X &= \sum\_{i = 1}^{n - 1}\sum\_{j = i + 1}^{n} X\_{ij} \\\\\\
E[X] &= E\bigg[\sum\_{i = 1}^{n - 1}\sum\_{j = i + 1}^{n} X\_{ij}\bigg] & \text{(by
taking expectation on both sides)}\\\\\\
&= \sum\_{i = 1}^{n - 1}\sum\_{j = i + 1}^{n} E\big[X\_{ij}\big] & \text{(by
linearity of expectation)} \\\\\\
&= \sum\_{i = 1}^{n - 1}\sum\_{j = i + 1}^{n} \frac{1}{2} \\\\\\
&= {n \choose 2} \frac{1}{2} \\\\\\
&= \frac{n \cdot (n - 1)}{2} \cdot \frac{1}{2} \\\\\\
&= \frac{n \cdot (n - 1)}{4}
\\end{align} 
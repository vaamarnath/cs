---
layout: default
title: The hiring problem
categories: clrs
---

###Solution 5.1-1
A relation that is reflexive, antisymmetric, and transitive is a **partial
order**. 
A relation $R$ on a set A is a **total relation** if for all $ a, b
\in A $, we have $a R b$ or $b R a$ (or both), that is, if every
pairing of elements of A is related by $R$.
A **partial order** that is also a total relation is a total order or
linear order.

In the given procedure, HIRE-ASSISTANT, we can trivially prove that the
comparison is partial order. And we can also come to the conclusion and for any
$ a, b \in A $, $a R b$ and $b R a$ exists. Hence, we have a total
order on the ranks of the candidates.

###Solution 5.1-2
The gist of this algorithm is to generate a $ c $ bit binary number using $ c $
calls to RANDOM(0, 1). Let's define $ n = b - a $. And $ c = \lceil \ln n \rceil
$. 


RANDOM\_BETWEEN\_A\_B($ a $, $ b $)

1. Evaluate $ c = \lceil \ln n \rceil $.

2. Invoke RANDOM(0, 1) $ c $ times to generate a $ c $ digit binary number, $
m $. 

3. If $ r > n $, return to step 1 to re-generate a new number.

4. Return $ a + r $.

Probability of getting a number in the range $ [a, b] $, $ p $ is $
\frac{n}{2^{c}} $ as we have $ n $ favorable choice versus a total number of $
2^{c} $ elements in the sample space. Now, to calculate the running time of the
algorithm, we need to look at the number of tries the algorithm has to perform
to get a random number. At step 3, if the condition is not met, the algorithm is
run again. Hence, each iteration can be looked as a Bernoulli trial with
probability $ p $ in our favor. The expected number of trials for this scenario
is $ c \cdot \frac{1}{p} $. Expected running time is,
\\[ 
  O\bigg(\frac{2^c}{n} c\bigg) = O\bigg(\frac{\ln(b-a)2^{\ln(b-a)}}{b-a}\bigg)
                                 = O(\ln(b-a))
\\]
                                 
###Solution 5.1-3
UNBIASED-RANDOM

1. $ x = $ BIASED\_RANDOM

2. $ y = $ BIASED\_RANDOM

3. If $ x \neq y $, return $ x $. Else, goto step 1.

Here, we keep on invoking BIASED\_RANDOM unless and until we obtain $ x \neq y
$. Observe,

Prob.\{$ x = 0 $ and $ y = 1 $\} = $(1 - p) p $,

Prob.\{$ x = 1 $ and $ y = 0 $\} = $p (1 - p) $. 

And we have probability of UNBIASED\_RANDOM returning $ 0 $ and $ 1 $ with the
same probability. $O(1)$ is the running time for each iteration of the
algorithm. The algorithm is successful whenever it returns $ 0 $ or $ 1 $. And,
probability for success is $ 2\cdot p \cdot (1 - p) $. And we can look at each trial as
Bernoulli trial. The expected number of trials is $ \frac{1}{2p(1 - p)} $. (As
the number of trials follows geometric distribution). Expected running time is $
\Theta(\frac{1}{2p(1 - p)}) $.

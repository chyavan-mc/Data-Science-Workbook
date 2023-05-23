# Probability Basics

## Basic Definitions

1. **Sample Space** - A sample space $\Omega$ associated with a random experiment is the set of all possible outcomes of the experiment

2. **Event** - An event $E$ is a subset of the sample space $\Omega$, or in other words a set of possible outcomes.

Both Sample Space and Event can be finite, countably infinite, or uncountably infinite. For example, consider a random experiment of throwing a dart at a round board without missing the board. Assuming the radius of the board is 1, the sample space is the set of all two dimensional vectors inside the unit circle - 
$$\Omega=\left\{(x,y)\,:\, x,y\in\mathbb{R}, \,\sqrt{x^2+y^2} < 1\right\}$$
An event describing a bullseye hit is - 
$$E=\left\{(x,y)\, : \,x,y\in\mathbb{R}, \,\sqrt{x^2+y^2} < 0.1\right\}\subset\Omega.$$

both the sample space $\Omega$ and the event $E$ are uncountably infinite

### Boole's Inequality
$$ P(\bigcup_{i} A_i) \leq \sum_i P(A_i)$$
This is derived from the equation $P(A \cup B) = P(A) + P(B) - \boxed{P(A \cap B)}$

## Conditional Probability

If A & B are two events and $P(B) > 0$,
$$P(A|B) = \frac{P(A \cap B)}{P(B)}$$

* If $A \subset B$, $P(A|B) = \frac{P(A)}{P(B)}$
* If $B \subset A$, $P(A|B) = \frac{P(B)}{P(B)} = 1$

### Pairwise Independence
A finite number of events $A_1, A_2, ... , A_n$ are pairwise independent if every pair $A_i, A_j, i \neq j$ are independent

### Independence
A finite number of events $A_1, A_2, ... , A_n$ are independent if every subset of event from the set of events is independent of every other subset of events. Independence implies - 
$$P(A_1 \cap A_2 \cap ... A_n) = P(A_1).P(A_2)...P(A_n)$$

### Conditional Independence
A and B are conditionally independent if
$$ P(A \cap B | C) = P(A|C).P(B|C) $$

### General Multiplication rule
$$ P (A_1 \cap A_2 \cap ... A_n) = P(A_1).P(A_2|A_1).P(A_3|A_1 \cap A_2)...P(A_n| A_1 \cap A_2 ... A_{n-1})$$

> **NOTE:**
> * Pairwise independence is a weaker condition than independence
> * If $A$ and $B$ are independent, $P(A|B) = P(A)$
> * If $A$ and $B$ are disjoint, $P(A|B) = 0$, meaning they are not independent
> * If $A$ and $B$ are independent, $A^c$ and $B$ are also independent

## Bayes Theorem
If A & B are two events and $P(A) \neq 0$, $P(B) \neq 0$,
$$P(A|B) = \frac{P(B|A).P(A)}{P(B)}$$

### Law of total probability
For an exhaustive set of events $A_1, A_2, ... , A_n$
$$P(B) = \sum_{i} P(B|A_i)(A_i)$$

## Binomial Theorem
$$ (x+y)^n = \sum_{i=0}^{n} {n \choose i} x^i y^{n-i} $$

## Random Variables

A random variable (RV) $X$ is a function from the sample space $\Omega$ to the real numbers $X:\Omega \to \mathbb{R}$. Assuming $E \subset R$ we denote the event $\{ \omega \in \Omega : X(\omega) \in E \} \subset \Omega $ by $X \in E$

> **Example:**
> Throwing two fair dice, $\Omega=\{ \omega = (a,b): a \in \{1,…,6\},b \in \{1,…,6\}\}$, the RV $X(a,b)=a+b$

* A random variable $X$ is discrete if $P(X \in K) = 1$ for some finite or countably infinite set $K \subset \mathbb{R}$.
* A random variable $X$ is continuous if $P(X=x)=0$ for all $x \in \mathbb{R}$

> **Example:**
> Throwing two fair dice, $\Omega=\{ \omega = (a,b): a \in \{1,…,6\},b \in \{1,…,6\}\}$, the RV $X(a,b)=a+b$


> **Example:**
> In the dart throwing experiment, the sample space is $\Omega=\{(x,y):\sqrt{x^2+y^2}<1\}$.
> * The RV $V$, which is 1 for a bullseye and 0 otherwise, is discrete since $P(V \in {0,1}) = 1$.
> * The RV $W$, defined as $W(x,y)=\sqrt{x^2+y^2}$, represents the distance of between the dart position and the origin. Since the 2-D area of a circle $\{W=w\} = \{(x,y):x,y \in \mathbb{R}, \sqrt{x^2+y^2}= w \}$ is zero for all w, $P(W=w)=Area(\{W=w\})/(π1^2)=0$ (under the classical model), implying that W is a continuous RV

### Probability Distributions

#### Cumulative Probability Distribution
We define the cumulative distribution function (cdf) with respect to an RV $X$ to be $F_X:\mathbb{R} \to \mathbb{R}$ given by $F_X(x) = P(X \leq x)$

#### Discrete RV - Probability Mass Function
Given a discrete RV $X$, we define the associated probability mass function (pmf) $p_X: \mathbb{R} \to \mathbb{R}$ to be $p_X(x)=P(X=x)$.

> **Example:**
> In the coin toss example
> $$\begin{align*}
p_X(x)=P(X=x)=\begin{cases} 1/8 & x=0 \\ 3/8 & x=1 \\ 3/8 & x=2\\
1/8 & x=3 \\ 0 & \text{else}
\end{cases} \qquad
F_X(x)=P(X\leq x)=\begin{cases} 0 & x < 0 \\ 1/8 & 0\leq x < 1 \\ 1/2 & 1\leq x <  2\\
7/8 & 2\leq x < 3 \\ 1 & 3 \leq x
\end{cases}.
\end{align*}$$

For the PMF
* $p_X(x) \geq 0$
* $\sum_x p_X(x) = 1$

#### Continuous RV - Probability Density Function
Given a continuous RV $X$, we define the associated probability density function (pdf) $f_X: \mathbb{R} \to \mathbb{R}$ as the derivative of the cdf $f_X=F'_X$ where it exists, and 0 elsewhere.

> **Example:**
> $$\begin{align*}
F_R(r)&=\P(R\leq r)=\begin{cases} 0 & r < 0 \\
\pi r^2 / (\pi 1^2)=r^2 & 0\leq r < 1\\
1 & 1\leq r
\end{cases}, \\
f_R(r)&=\frac{dF_R(r)}{dr}=\begin{cases} 0 &  r<0 \\
2r & 0\leq r <1\\
0 & 1\leq r
\end{cases}.
\end{align*}$$
> **NOTE:** The PDF can have a value greater than 1

For the PDF
* $f_X$ is a non-negative function
* $\int_{\R} f_X(x)dx=1$
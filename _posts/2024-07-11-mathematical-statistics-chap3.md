---
layout: post
title: "Mathematical Statistics Cheatsheet: Chapter 3"
categories: [Mathematics, Statistics, Lecture Notes]
excerpt: "Random Variables, Probability Distributions, Continuous Random Variables, Probability Density Functions, Multivariate Distributions, Marginal Distributions, Conditional Distributions, The Theory in Practice"
---

Note: (*) means that bullet point is not mentioned in class but in handout.

# Discrete Random Variable

- X is a **random variable** if: S is a sample space with a probability measure and X is a **real-valued function** defined over the elements of S.

- **Real-valued functions** are functions that take a real number or a vector consisted of real numbers as their input values.

- Random variables denoted by **capital** letters.

- **X = x** is the set of elements in the sample space for which the random variable X has value x.

- The **probability distribution** of a **discrete** random variable X, or **probability mass function**, or **p.m.f.** of X, is: the function given by $f(x) = P(X = x)$ for each x within the range of X.

- **Rules** of probability distribution fuctions:
    1. $f(x) \geq 0$ for each value within its domain.
    2. $\sum_{x}f(x) = 1$ for $x \in D$.

- The **distribution function**, or the **cumulative distribution**, of a discrete random variable X, or **cumulative distribution function**, or **c.d.f.**: the function given by $$F(x) = P(X \leq x) = \sum_{t \leq x}f(t) \text{ for } -\infty < x < \infty$$, where $f(t)$ is the value of the probability distribution of X at t.

- **Rules** of cumulative distribution function F:
    1. $F(-\infty) = 0$, and $F(\infty) = 1$,
    2. if $a < b$, then $F(a) \leq F(b)$ for any real numbers a and b.

- **Theorem 3.3**: if the range of a random variable X consists of the values $x_1 < x_2 < x_3 < ... < x_n$, then $f(x_1) = F(x_1)$ and $f(x_i) = F(x_i) - F(x_i-1) \text{ for } i = 2, 3, 4, ..., n$.

# Continuous Random Variable

- **A probability density function (p.d.f.)** of the continuous random variable X, is: a function with values over the set of all real numbers such that $P(a \leq x \leq b) = \int_{a}^{b}f(x)dx$ for any real constants a and b with $a \leq b$.

- **Probability density function syncronoms**: probability densities, density functions, densities.

- **P(X = c) = 0** for any real constant c if X is a **continuous** random variable.

- **Rules of probability density functions**: 
    1. $f(x) \geq 0 \text{ for } -\infty < x < \infty$,
    2. $\int_{-\infty}^{\infty}f(x)dx = 1$.

- The **distribution function** of Y, a **continuous** random variable, is: $F(y)$ such that $F(y)= P(Y \leq y) \text{ for } −\infty < y  < \infty$.

- **Theorem 3.6**: Given f(x) and F(x) for a continuous random variable X, then $$P(a \leq X \leq b) = F(b) - F(a)$$ for any real number a, b with $a \leq b$ and $f(x) = \frac{dF(x)}{dx} = F'(x)$ where F is differentiable.

# Multivariate Distributions: Discrete Random Variable

- The **joint probability distribution** of discrete random variables X and Y, is: $f(x, y) = P(X = x, Y = y)$ for each pair of values $(x, y)$ within the range of X and Y.

- **Rules of joint probability distributions**:
    1. $f(x, y) \geq 0$ for each pair of values (x, y) within its domain,
    2. $\sum_{x} \sum_{y} f(x, y) = 1$, double summations extends over all pairs $(x, y) \in D$.

- **The joint distribution function**, or the **joint cumulative distribution** of **discrete** random variables X and Y is given by $F(x, y) = P(X \leq x, Y \leq y) = \sum_{s \leq x} \sum_{t \leq y} f(s, t) \text{ for } -\infty < x < \infty, -\infty < y < \infty$.

# Multivariate Distributions: Continuous Random Variable

- **A joint probability density function** (or, **joint p.d.f.**) of the **continuous** random variables X and Y, is: a bivariate function with values f(x, y) defined over the xy-plane, such that $P[(X, Y) \in A] = \int \int_{A} f(x, y)dxdy$ for any area A in the xy-plane.

- **Rules of p.d.f.**:
    1. $f(x, y) \geq 0 \text{ for } -\infty < x < \infty, -\infty < y < \infty$,
    2. $\int \int_{R^2}f(x, y)dA = \int_{-\infty}^{\infty} \int_{-\infty}^{\infty} f(x, y)dxdy = 1$.

- **The joint distribution function** or **the joint cumulative distribution** of **continuous** random variables X and Y, is: $F(x, y) = P(X \leq x, Y \leq y) = \int_{-\infty}^{x} \int_{-\infty}^{y} f(s, t)dsdt \text{ for } -\infty < x < \infty \text{, } -\infty < y < \infty$.

- $f(x, y) = \frac{\partial^2}{\partial{x}\partial{y}}F(x, y)$

- (*)**Trivariate, ..., multivariate** case: $F(x_1, x_2, ..., x_n) = P(X_1 \leq x_1, X_2 \leq x_2, ... X_n \leq x_n) = \int_{-\infty}^{x_n} ... \int_{-\infty}^{x_2} \int_{-\infty}^{x_1}f(t_1, t_2, ..., t_n)dt_1dt_2...dt_n$, $-\infty < x_i < \infty$, $i = 1, 2, ..., n$, $f(t_1, t_2, ..., t_n) = P(X_1 = x_1, X_2 = x_2, ... X_n = x_n) = \frac{\partial^n}{\partial{x_1} \partial{x_2} ...\partial{x_3}}F(x_1, x_2, ..., x_n)$.

# Marginal Distributions

- Given **discrete** random variables X, Y with joint probability function f(x, y) at x, y, the **marginal distribution of X** is: $g(x) = \sum_{y}f(x, y)$ for each x within the range of X, 

the **marginal distribution of Y** is: $h(y) = \sum_{x}f(x, y)$ for each y within the range of Y.

- Given **continuous** random variables X, Y with joint probability function f(x, y) at x, y, the **marginal density of X** is: $g(x)=\int_{-\infty}^{\infty}f(x,y)dy \text{ for } -\infty < x < \infty$

the **marginal density of Y** is: $h(y) = \int_{-\infty}^{\infty}f(x,y)dx \text{ for } -\infty < y < \infty$.

- **Joint marginal distributions**
    - **Discrete**: 
        - $X_1$'s marginal distribution: $g(x_1) = \sum_{x_2}...\sum_{x_n}f(x_1, x_2, ..., x_n)$.
        - $X_1, X_2, X_3$'s marginal distribution: $m(x_1, x_2, x_3) = \sum_{x_4}...\sum_{x_n}f(x_1, x_2, ..., x_n)$.
    - **Continuous**:
        - $X_2$'s marginal distribution: $h(x_2) = \int_{-\infty}^{\infty}...\int_{-\infty}^{\infty}f(x_1, x_3, ..., x_n)dx_1dx_3...dx_n$.
        - $X_1, X_n$'s marginal distribution: $\phi(x_1, x_n) = \int_{-\infty}^{\infty}...\int_{-\infty}^{\infty}f(x_2, x_3, ..., x_{n-1})dx_2dx_3...dx_{n-1}$.

# Conditional Distributions

- The **conditional distribution** of X given Y = y, **discrete** randome variables X and Y with f(x, y) the joint probability distribution, h(y) the marginal distribution of Y at y: $f(x \mid y) = \frac{f(x, y)}{h(y)}$, $h(y) \neq 0$ for each x within the range of X.

- The **conditional distribution** of Y given X = x, **discrete** randome variables X and Y, g(x) the marginal distribution of X at x: $w(y \mid x) = \frac{f(x, y)}{g(x)}$, $g(x) \neq 0$ for each y within the range of Y.

- The **conditional density** of X given Y = y, **continuous** randome variables X and Y with f(x, y) the joint probability distribution, h(y) the marginal distribution of Y at y: $f(x \mid y) = \frac{f(x, y)}{h(y)}$, $h(y) \neq 0$ for $-\infty < x < \infty$.

- The **conditional density** of Y given X = x, **continuous** randome variables X and Y, g(x) the marginal distribution of X at x: $w(y \mid x) = \frac{f(x, y)}{g(x)}$, $g(x) \neq 0$ for $-\infty < y < \infty$.

- Reasoning behind the definitions:
    - We have the definition of conditional probability of event A given event B: $P(A \mid B) = \frac{P(A \cap B)}{P(B)}$. Let A be $X = x$ and B be $Y = y$, then $P(X = x \mid Y = y) = \frac{P(X = x, Y = y)}{P(Y = y)} = \frac{f(x, y)}{h(y)}$, given $h(y) \neq 0$.

- Conditional distributions/densities with **multiple variables**:
    - Given **four discrete random variables**, the conditional distribution of $X_3$ at $x_3$ given $X_1 = x_1, X_2 = x_2, X_4 = x_4$ is: $p(x_3 \mid x_1, x_2, x_3) = \frac{f(x_1, x_2, x_3, x_4)}{g(x_1, x_2, x_4)}$, $g(x_1, x_2, x_4) \neq 0$ where $g(x_1, x_2, x_4)$ is the joint marginal distribution of $X_1, X_2, X_4$.
    - The **joint conditional distribution** of $X_2, X_4$ at $(x_2, x_4)$ is: $p(x_2, x_4 \mid x_1, x_3) = \frac{f(x_1, x_2, x_3, x_4)}{m(x_1, x_3)}$, $m(x_1, x_3) \neq 0$.
    - The **joint conditional distribution** of $X_2, X_3, X_4$ at $(x_2, x_3, x_4)$ is: $p(x_2, x_3, x_4 \mid x_1) = \frac{f(x_1, x_2, x_3, x_4)}{b(x_1)}$, $b(x_1) \neq 0$.

- n **discrete** random variables are **independent** if and only if $f(x_1, x_2, ..., x_n) = f_1(x_1) \cdot f_2(x_2) ... \cdot f_ n(x_n)$ for all $(x_1, x_2, ..., x_n)$ within range where $f_i(x_i)$ is the **marginal distribution** function of $X_i$ at $x_i$.
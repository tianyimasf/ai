---
layout: post
title: "Mathematical Statistics Cheatsheet: Chapter 3"
categories: [Mathematics, Statistics, Lecture Notes]
excerpt: "Random Variables, Probability Distributions, Continuous Random Variables, Probability Density Functions, Multivariate Distributions, Marginal Distributions, Conditional Distributions, The Theory in Practice"
---

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

# Multivariate Distributions
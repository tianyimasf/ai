---
layout: post
title: "Mathematical Statistics Cheatsheet: Chapter 3"
categories: [Mathematics, Statistics, Lecture Notes]
excerpt: "Random Variables, Probability Distributions, Continuous Random Variables, Probability Density Functions, Multivariate Distributions, Marginal Distributions, Conditional Distributions, The Theory in Practice"
---

- X is a **random variable** if: S is a sample space with a probability measure and X is a **real-valued function** defined over the elements of S.

- **Real-valued functions** are functions that take a real number or a vector consisted of real numbers as their input values.

- Random variables denoted by **capital** letters.

- **X = x** is the set of elements in the sample space for which the random variable X has value x.

- The **probability distribution** of a **discrete** random variable X, or **probability mass function**, or **p.m.f.** of X, is: the function given by $f(x) = P(X = x)$ for each x within the range of X.

- **Rules** of probability distribution fuctions:
    1. $f(x) \geq 0$ for each value within its domain.
    2. $\sum_{x}f(x) = 1$ for $x \in D$.

- The **distribution function**, or the **cumulative distribution**, of a discrete random variable X, or **cumulative distribution function**, or **c.d.f.**: the function given by $$F(x) = P(X \leq x) = \sum_{t \leq x}f(t) \text{ for } -\infty < x < \infty$$, where $f(t)$ is the value of the probability distribution of X at t.
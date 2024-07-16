---
layout: post
title: "Mathematical Statistics Cheatsheet: Chapter 5"
categories: [Mathematics, Statistics, Lecture Notes]
excerpt: "Introduction, The Discrete Uniform Distribution, The Bernoulli Distribution, The Binomial Distribution, The Negative Binomial and Geometric Distributions, The Hypergeometric Distribution, The Poisson Distribution, The Multinomial Distribution, The Multivariate Hypergeometric Distribution, The Theory in Practice"
---

Note: (*) means that bullet point is not mentioned in class but in handout.

- A **discrete uniform distribution** of a random variable X, which is referred to a discrete uniform random variable if and only if its probability distribution is: \[f(x) = \frac{1}{k} \text{ for } x = x_1, x_2, ..., x_k \text{, where } x_i \neq x_j \text{, when } i \neq j\]

- $\mu = \sum_{i = 1}^k x_i \cdot \frac{1}{k}$

- $\sigma^2 = \sum_{i = 1}^k (x_i - \mu)^2 \cdot \frac{1}{k}$

- If $x_i = i, \mu = \frac{k+1}{2}, \sigma^2 = \frac{k^2-1}{12}, M_X(t) = \frac{e^t(1 - e^{kt})}{k(1-e^t)}$

- A **Bernoulli distribution** of a random variable X, which is referred to a Bernoulli random variable if and only if its probability distribution is: \[f(x; \theta) = \theta^X(1 - \theta)^{1-X} \text{, for } x = 0, 1\] where $\theta$ = probability of **success** (e.g. heads) and $1 - \theta$ = probability of **failure** (e.g. tails).

- $f(0; \theta) = 1 - \theta$, $f(1; \theta) = \theta$.

- A **Binomial distribution** of a random variable X, which is referred to a binomial random variable if and only if its probability distribution is: \[b(x; n, \theta) = C(n, x)\theta^X(1 - \theta)^{n-x} \text{, for } x = 0, 1, 2, ..., n\] where $C(n, x)$ is n choose x, and **x successes in n** (e.g. tossing balanced coins 10 times, get x = 4 heads and n - x = 6 tails) independent and identical Bernoulli **trials**.

- **Cumulative probability** of a binomial random variable X is: $P(X \leq x) = B(x; n, \theta) = \sum_{k=0}^{x}b(k; n, \theta)$.

- $b(x; n, \theta) = b(n - x; n, 1 - \theta)$.

- **Mean**: $\mu = n\theta$; **variance**: $\sigma^2 = n\theta(1 - \theta)$.

- **Theorem 5.3**: if X a binomial random variable and $Y = \frac{X}{n}$, then \[ \mu_Y = E(Y) = \theta \text{ and } \theta_Y^2 = \frac{\theta(1 - \theta)}{n} \]
    - Proof: use $E(aX) = aE(X)$ and $var(aX) = a^2var(X)$.

- **Law of large numbers**: we apply Chebyshev's Theorem to the proportion of success, which is $Y = \frac{X}{n}$. 
    - Let $k\sigma = c$ for any constant $c > 0$, by Chebyshev's Theorem, the proportion of success in n trials falls between $\theta - c$ and $\theta + c$ is at least \[1 - (\frac{\sigma}{c})^2 \Rightarrow 1 - \frac{\theta(1 - \theta)}{nc^2}\] by plugging in $\sigma_Y^2 = \frac{\theta(1 - \theta)}{n}$ from the previous theorem. 
    - As $n \rightarrow \infty$, this probability approaches 1. 
    - This means that the porprotion of success will different from $\theta$ by less than any arbitrary constant c.
    - It makes sense because the definition of $\theta$ is the rate of success. 

- The **binomial distribution**'s moment-generating function is: $M_X(t) = [1 + \theta(e^t - 1)]^n$.

- $M_X'(t) = n\theta e^t[1 + \theta(e^t - 1)]^(n-1)$

- $M_X''(t) = n\theta e^t(1 - \theta + n\theta e^t)[1 + \theta(e^t - 1)]^(n-2)$

- Substitue for $t = 0$, we get $\mu_1' = n\theta$, $\mu_2' = n\theta(1 - \theta) \rightarrow \mu = n\theta, \sigma^2 = \mu_2' - \mu^2 = n\theta(1 - \theta) - (n\theta)^2 = n\theta(1 - \theta)$

- The **r-th factorial moment**: $\mu_{(r)}' = E[X(X - 1)(X - 2)...(X - r + 1)]$.

- The **factorial moment-generating function**: $F_X(t) = E(t^X) = \sum_X t^X \cdot f(x)$.

- The r-th factorial moment of $F_X(t) w.r.t t = 1$ is $\mu_{(r)}'$ the r-th factorial moment.

- A **negative binomial distribution** of a random variable X which would be referred to as a negative binomial random variable if and only if \[b^*(x; k, \theta) = C(x - 1, k - 1)\theta^k(1 - \theta)^{x-k} \text{, for } x = k, k+1, k+2, ...\] where **the k-th success will occur on the x-th trial** (e.g. at trial number 10, a head appeared for the 6-th time when tossing a balanced coin).

- **Alternative names**: **binomial waiting-time distribution/Pascal distribution**.

- **Reason for the name**: the name derives from the fact that the values of the probability distribution are the terms of binomial expansion of $(\frac{1}{\theta} - \frac{1 - \theta}{\theta})^{-k}$ (notice it's the fraction to the power of **negative** k).

- **Theorem 5.5**: $b^*(x; k, \theta) = \frac{k}{x}\cdot b(k; x, \theta)$.

- **Mean** of **negative binomial distribution**: $\mu = \frac{k}{\theta}$.

- **Variance** of **negative binomial distribution**: $\sigma^2 = \frac{k}{\theta}(\frac{1}{\theta} - 1)$.

- A **geometric distribution** of a random variable X which would be referred to as a geometric random variable if and only if \[g(x; \theta) = \theta(1 - \theta)^{x-1} \text{, for } x = 1, 2, 3, ...\] where **the first sucess will occur at x-th trial** (e.g. at trial number 3, after tossing a balanced coin 2 times, at the third time, the first head appears).
    - This is equivalent to **the negative binomial distribution with k = 1**.

- Trials are assumed to be **independent** of each other.

# The Hypergeometric Distribution

- This distribution consider getting x success in n trials when **without replacement** choosing n of the N elements contained in the sample space/set and is therefore different from previous probability distributions.

- **Deducing the formula**: assume there are M success elements in set with N elements.
    1. There are $M \choose x$ ways of choosing x of the M successes, and
    2. $N - M \choose n - x$ ways of choosing n - x of N - M failures.
    3. In total there are $N choose n$ ways of choosing n of the N elements in the set.
    4. Assuming all permutations of the n elements are all equaly likely, the probability of **x successes is contained in n trials** is: $\frac{ {M \choose x} {N - M \choose n - x} }{N \choose n}$.

- A **hypergeometric distribution** of a random variable X which would be referred to as a hypergeometric random variable if and only if \[h(x; n, N, M) = \frac{ {M \choose x} {N - M \choose n - x} }{N \choose n} \text{, for } x = 0, 1, 2, ..., n, x \leq M \text{ and } n - x \leq N - M\]

- **Mean** of **hypergeometric distribution**: $\mu = \frac{nM}{N}$.

- **Variance** of **hypergeometric distribution**: $\sigma^2 = \frac{NM(N - M)(N - n)}{N^2(N - 1)}$.

# The Poisson Distribution

- Let $\lambda = n\theta$, by definition this represents the average number of successes after n trials. 

- Rearranging the formula gives us $\theta = \frac{\lambda}{n}$. As $n \rightarrow \infty$, $\theta \rightarrow 0$. 
    - This means that as we conduct more trials, if the number of successes remains constant, then that means the rate of success($\theta$) is close to 0. 
    - Because if the rate of success($\theta$) is positive, more successes will occur eventually. If this is not true, then the rate of success($\theta$) is near 0. 

- Plug $\lambda = n\theta$ in the definition of the binomial distribution, then: $ b(x; n, \theta) = {n \choose x} (\frac{\lambda}{n})^x (1 - \frac{\lambda}{n}^(n - x)) = \frac{n(n-1)...(n-x+1)}{x!}(\frac{\lambda}{n})^x(1 - \frac{\lambda}{n})^{n-x} $ $= \frac{1(1-\frac{1}{n})(1-\frac{2}{n})...(1-\frac{x-1}{n})}{x!}(\lambda)^x[(1-\frac{\lambda}{n})^{-\frac{n}{\lambda}}]^{-\lambda}(1 - \frac{\lambda}{n})^{-x} \rightarrow \frac{1}{x!}\cdot \lambda^x e^{-\lambda} = \frac{\lambda^x e^{-\lambda}}{x!}$

- The Poisson distribution gives the probability of an event happening a certain number of times($\lambda$) within a given number of trials (n).

- In general, the Poisson gives a good approximation to binomial probabilities when $n \leq 20$, and $\theta \leq 0.05$. 
    - When $n \leq 100, n\theta < 10$, the approximation is generally excellant.
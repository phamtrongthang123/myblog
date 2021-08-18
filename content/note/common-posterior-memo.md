---
title: "Common Posterior distribution memo"
date: "2021-08-18"

tags: 
- Note 
- EN
---

**and their related information, theorem, corollary, ...** 



# Introduction

I don't want to look up wiki too much for common distribution so I write them all here. The title is posterior, but actually I write all information that I may look up later. They probably useless most of the time, but well, it's better than looking up all stuff from scratch.

The main motivation is to look up posterior later, so that's the name. But what if I forget the whole properties of the distribution? That's why there are addition information.

The date will be updated for each time I update this document. 

## Discrete distribution



### Bernoulli and Binomial

**Bernoulli distribution**
If `$X$` is a random variable with this distribution, then:
`$$
\operatorname{Pr}(X=1)=p=1-\operatorname{Pr}(X=0)=1-q
$$`
The probability mass function `$f$` of this distribution, over possible outcomes `$k$`, is
`$$
f(k ; p)= \begin{cases}p & \text { if } k=1, \\ q=1-p & \text { if } k=0\end{cases}
$$`
This can also be expressed as
`$$
f(k ; p)=p^{k}(1-p)^{1-k} \quad \text { for } k \in\{0,1\}
$$`
or as
`$$
f(k ; p)=p k+(1-p)(1-k) \quad \text { for } k \in\{0,1\} .
$$`

**Binomial distribution**

In general, if the random variable `$X$` follows the binomial distribution with parameters `$n \in \mathbb{N}$` and `$p \in[0,1]$`, we write `$X \sim \mathrm{B}(n, p) .$` The probability of getting exactly `$k$` successes in `$n$` independent Bernoulli trials is given by the probability mass function:
`$$
f(k, n, p)=\operatorname{Pr}(k ; n, p)=\operatorname{Pr}(X=k)=\left(\begin{array}{l}
n \\
k
\end{array}\right) p^{k}(1-p)^{n-k}
$$`
for `$k=0,1,2, \ldots, n$`, where
`$$
\left(\begin{array}{l}
n \\
k
\end{array}\right)=\frac{n !}{k !(n-k) !}
$$`


### Hypergeometric  distribution

A random variable `$X$` follows the hypergeometric distribution if its probability mass function is given by
`$$
p_{X}(k)=\operatorname{Pr}(X=k)=\frac{\left(\begin{array}{c}
K \\
k
\end{array}\right)\left(\begin{array}{c}
N-K \\
n-k
\end{array}\right)}{\left(\begin{array}{c}
N \\
n
\end{array}\right)}
$$`
where
- `$N$` is the population size,
- `$K$` is the number of success states in the population,
- `$n$` is the number of draws (i.e. quantity drawn in each trial),
- `$k$` is the number of observed successes,
- `$\left(\begin{array}{l}a \\ b\end{array}\right)$` is a binomial coefficient.

**Note about binomial and hypergeometric distribution**

​	Both are a bunch of Bernoulli trial, but Hypergeometric is draw without replacement, hence the trials are dependent, unlike Binomial are independent. 



### Multinomial distribution

Suppose one does an experiment of extracting *n* balls of *k* different colors from a bag, replacing the extracted balls after each draw. Balls of the same color are equivalent. Denote the variable which is the number of extracted balls of color `$i(i=1, \ldots, k)$` as `$X_{i}$`, and denote as `$p_{i}$` the probability that a given extraction will be in color `$i$. The probability mass function of this multinomial distribution is:

`$$
\begin{aligned}
 f\left(x_{1}, \ldots, x_{k} ; n, p_{1}, \ldots p_{k}\right) &=\operatorname{Pr}\left(X_{1}=x_{1} \text { and } \ldots \text { and } X_{k}=x_{k}\right) \\
&= \begin{cases}\frac{n !}{x_{1} ! \cdots x_{k} !} p_{1}^{x_{1}} \times \cdots \times p_{k}^{x_{k}}, & \text { when } \sum_{i=1}^{k} x_{i}=n \\
0 & \text { otherwise }\end{cases}
\end{aligned}
$$`
for non-negative integers `$x_{1}, \ldots, x_{k}$
The probability mass function can be expressed using the gamma function as:
`$$
f\left(x_{1}, \ldots, x_{k} ; p_{1}, \ldots, p_{k}\right)=\frac{\Gamma\left(\sum_{i} x_{i}+1\right)}{\prod_{i} \Gamma\left(x_{i}+1\right)} \prod_{i=1}^{k} p_{i}^{x_{i}}
$$`
This form shows its resemblance to the Dirichlet distribution, which is its conjugate prior.



Another way to say multinomial distribution is there is 1 dice with k faces with different probabilities, toss n times, then count the number of each face. Whereas in Binomial, we toss a coin.

### Discrete uniform distribution

Basically give all elements of an array the same chance of drawing. 

Let `$C$` be a finite, nonempty set of numbers. Choose one of these numbers uniformly at random (i.e., all values in `$C$` are equally likely). Call the chosen number `$X$`. Then `$X$` is said to have the Discrete Uniform distribution with parameter `$C ;$` we denote this by `$X \sim \operatorname{DUnif}(C)$`. The PMF of `$X \sim \operatorname{DUnif}(C)$` is
`$$
P(X=x)=\frac{1}{|C|}
$$`


### Poison distribution

A discrete random variable `$X$` is said to have a Poisson distribution, with parameter `$\lambda>0$`, if it has a probability mass function given by:
`$$
f(k ; \lambda)=\operatorname{Pr}(X=k)=\frac{\lambda^{k} e^{-\lambda}}{k !}
$$`
where
- `$k$` is the number of occurrences `$(k=0,1,2 \ldots)$` 
- `$e$` is Euler's number `$(e=2.71828 \ldots)$`
- ! is the factorial function.
The positive real number `$\lambda$` is equal to the expected value of `$X$` and also to its variance 

`$$
\lambda=\mathrm{E}(X)=\operatorname{Var}(X)
$$`



## Continuous distribution

### Uniform distribution

The probability density function of the continuous uniform distribution is:
`$$
f(x)= \begin{cases}\frac{1}{b-a} & \text { for } a \leq x \leq b, \\ 0 & \text { for } x<a \text { or } x>b\end{cases}
$$`


### Normal (Gaussian) distribution

The general form of its probability density function is
`$$
f(x)=\frac{1}{\sigma \sqrt{2 \pi}} e^{-\frac{1}{2}\left(\frac{x-\mu}{\sigma}\right)^{2}}
$$`

### Exponential distribution

The probability density function (pdf) of an exponential distribution is
`$$
f(x ; \lambda)= \begin{cases}\lambda e^{-\lambda x} & x \geq 0 \\ 0 & x<0\end{cases}
$$`


## Conjugate distribution

Conjugate priors are useful because they reduce Bayesian updating to modifying the parameters of the prior distribution (so-called hyperparameters) rather than computing integrals.

### Beta distribution

The probability density function (pdf) of the beta distribution, for `$0 \leq x \leq 1$`, and shape parameters `$\alpha, \beta>0$`, is a power function of the variable `$x$` and of its reflection `$(1-x)$` as follow:
`$$
\begin{aligned}
f(x ; \alpha, \beta) &=\text { constant } \cdot x^{\alpha-1}(1-x)^{\beta-1} \\
&=\frac{x^{\alpha-1}(1-x)^{\beta-1}}{\int_{0}^{1} u^{\alpha-1}(1-u)^{\beta-1} d u} \\
&=\frac{\Gamma(\alpha+\beta)}{\Gamma(\alpha) \Gamma(\beta)} x^{\alpha-1}(1-x)^{\beta-1} \\
&=\frac{1}{\mathrm{~B}(\alpha, \beta)} x^{\alpha-1}(1-x)^{\beta-1}
\end{aligned}
$$`
where `$\Gamma(z)$` is the gamma function. The beta function, `$B$`, is a normalization constant to ensure that the total probability is 1.

**Gamma function**

For positive integer n
`$$
\Gamma(n)=(n-1) !
$$`
But gamma function is an extension of factorial function for complex number, for complex z it is 
`$$
\Gamma(z)=\int_{0}^{\infty} x^{z-1} e^{-x} d x, \quad \Re(z)>0
$$`
notice, the real part of z must be positive. 



### Dirichlet distribution

The Dirichlet distribution of order `$K \geq 2$` with parameters `$\alpha_{1}, \ldots, a_{K}>0$` has a probability density function
`$$
f\left(x_{1}, \ldots, x_{K} ; \alpha_{1}, \ldots, \alpha_{K}\right)=\frac{1}{\mathrm{~B}(\boldsymbol{\alpha})} \prod_{i=1}^{K} x_{i}^{\alpha_{i}-1}
$$`
where `$\left\{x_{k}\right\}_{k=1}^{k=K}$` belong to the standard `$K-1$` simplex, or in other words: `$\sum_{i=1}^{K} x_{i}=1$` and `$x_{i} \geq 0$` for all `$i \in\{1, \ldots, K\}$`
The normalizing constant is the multivariate beta function, which can be expressed in terms of the gamma function:
`$$
\mathrm{B}(\boldsymbol{\alpha})=\frac{\prod_{i=1}^{K} \Gamma\left(\alpha_{i}\right)}{\Gamma\left(\sum_{i=1}^{K} \alpha_{i}\right)}, \quad \boldsymbol{\alpha}=\left(\alpha_{1}, \ldots, \alpha_{K}\right)
$$`

### Normal distribution

Normal distribution is conjugate prior distribution of .. normal distribution. Well, there is nothing to say here.



# Posterior distribution

Posterior is considered when you are doing Bayesian inference. 

1. We choose a prior distribution `$\pi(\theta)$` that expresses our beliefs about a parameter `$\theta$` before we see any data.
2. We choose a distribution `$p(\mathrm{x} \mid \theta)$` that reflects our beliefs about `$\mathrm{x}$` given `$\theta$.
3. After observing data `$\mathcal{D}_{n}=\left\{X_{1}, \ldots, X_{n}\right\}$`, we update our beliefs and calculate the posterior distribution `$p\left(\theta \mid \mathcal{D}_{n}\right)$`.



By Bayes' theorem, the posterior distribution can be written as
`$$
p\left(\theta \mid X_{1}, \ldots, X_{n}\right)=\frac{p\left(X_{1}, \ldots, X_{n} \mid \theta\right) \pi(\theta)}{p\left(X_{1}, \ldots, X_{n}\right)}=\frac{\mathcal{L}_{n}(\theta) \pi(\theta)}{c_{n}} \propto \mathcal{L}_{n}(\theta) \pi(\theta)
$$`
where `$\mathcal{L}_{n}(\theta)=\prod_{i=1}^{n} p\left(X_{i} \mid \theta\right)$` is the likelihood function and
`$$
c_{n}=p\left(X_{1}, \ldots, X_{n}\right)=\int p\left(X_{1}, \ldots, X_{n} \mid \theta\right) \pi(\theta) d \theta=\int \mathcal{L}_{n}(\theta) \pi(\theta) d \theta
$$`
is the normalizing constant, which is also called the evidence.



You may ask, why would we want a prior distribution about parameter, and posterior also about posterior? 

Well, the thing about Bayes is we want to focus on the belief. At first we have belief without data, then we have belief updated by data. It is a belief about the process, the model, the distribution. 

Even I'm saying that, I know some people may confuse because the parameters does not sound very important. It is important to generate the data, to define the distribution, but it does not have the concrete meaning like "is it raining". 

Well, it is right and wrong. Some are true that does not have that meaning. But in Bayes, when we do Bayes net, there are params that are actually another random variables. So it does have meaning.

In Bayes inference, everything have their meaning, and should have. Notations are just notations. Just as a way to visualize the idea. 

By the way, we also can derive Bayesian prediction so we can do anything we want, don't worry. 



Actually, there is another problem we have to solve is how to compute the likelihood. Luckily for discrete distribution, the formula is the same as probability. For continuous distribution, we have to follow the general formula. Another thing to remember, likelihood function is a function of parameters, not the variable.

## Bernoulli - Beta

Let's say we have prior `$\pi(\theta)$` is `$\operatorname{Beta}\left(\alpha_{1}, \alpha_{0}\right) .$` 

Now, we observe `$M[1]$` heads and `$M[0]$` tails. It follows easily that:
`$$
\begin{aligned}
P(\theta \mid \mathcal{D}_{n}) & \propto \prod_{i=1}^{n} P\left(X_{i} \mid \theta\right)\pi(\theta) \\
& \propto \theta^{M[1]}(1-\theta)^{M[0]} \cdot \theta^{\alpha_{1}-1}(1-\theta)^{\alpha_{0}-1} \\
&=\theta^{\alpha_{1}+M[1]-1}(1-\theta)^{\alpha_{0}+M[0]-1}
\end{aligned}
$$`
which is precisely `$\operatorname{Beta}\left(\alpha_{1}+M[1], \alpha_{0}+M[0]\right) .$` 

Notice, this is the same for Binomial - Beta, because when it come down to 1 observation `$P\left(X_{i} \mid \theta\right)$` , it is a Bernoulli. The funny thing is people tend to use Binomial and Bernoulli interchangeably so if you don't know this fact, you may get into trouble. 

## Multinomial - Dirichlet

Let `$\boldsymbol{X} \sim \operatorname{Multinomial}(n, \boldsymbol{\theta})$` where `$\boldsymbol{\theta}=\left(\theta_{1}, \ldots, \theta_{K}\right)^{T}$` be a `$K$`-dimensional parameter `$(K>1)$`,  `$\boldsymbol{X}_{i}=\left(X_{i 1}, \ldots, X_{i K}\right)$`

If
`$$
\boldsymbol{\theta} \sim \operatorname{Dirichlet}(\boldsymbol{\alpha}) \text{ and }\boldsymbol{X}_{i} \mid \boldsymbol{\theta} \sim \operatorname{Multinomial}(\boldsymbol{\theta}) \text{ for }i=1,2, \ldots, n
$$`
then the posterior satisfies
`$$
p\left(\boldsymbol{\theta} \mid \boldsymbol{X}_{1}, \ldots, \boldsymbol{X}_{n}\right) \propto \mathcal{L}_{n}(\theta) \pi(\theta) \propto \prod_{i=1}^{n} \prod_{j=1}^{K} \theta_{j}^{X_{i j}} \prod_{i=1}^{K} \theta_{j}^{\alpha_{j}-1}=\prod_{i=1}^{K} \theta_{j}^{\sum_{i=1}^{n} X_{i j}+\alpha_{j}-1}
$$`
We see that the posterior is also a Dirichlet distribution:
`$$
\boldsymbol{\theta} \mid \boldsymbol{X}_{1}, \ldots, \boldsymbol{X}_{n} \sim \operatorname{Dirichlet}(\alpha+n \overline{\boldsymbol{X}})
$$`
where `$\overline{\boldsymbol{X}}=n^{-1} \sum_{i=1}^{n} \boldsymbol{X}_{i}$`

There is another condition about simplex here, I will update it later. 


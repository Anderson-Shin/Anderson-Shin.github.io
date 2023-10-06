---
title: "Some basic knowledge of distribution"
collection: statistics
permalink: /statistics/basic_knowledge_1
excerpt: 'Some of features of discrete and continuous distribution'
date: 2023-10-07
venue: 'Statistics post 1'
---

# Discrete Random Variables vs. Continuous Random Variables

## Discrete Random Variables
- Take on a countable set of distinct values.
- Often represent outcomes of countable events or experiments.
- Probability mass function (PMF) defines the probabilities of each possible value.

### Example: Poisson Distribution
- Models the number of events in a fixed interval of time or space, given a known average rate which is $\lambda$.
- PMF : P(X = k) = $\frac{e^{-\lambda} \cdot \lambda^k}{k!}$ 

![Poisson PMF](https://upload.wikimedia.org/wikipedia/commons/thumb/1/16/Poisson_pmf.svg/330px-Poisson_pmf.svg.png)
- Graphs such as bar charts, histograms, or probability mass functions.
- Gaps between values due to discrete nature.
- **Expectation (Mean):** The expected value of a Poisson-distributed random variable $X$ is $E[X] = \lambda$.

## Continuous Random Variables
- Can take on any value within a certain range.
- Typically model measurements and real-world quantities.
- Probability density function (PDF) describes the distribution of values.

### Example: Exponential Distribution
- Models the time between events in a Poisson process.
- PDF : $f(x)$ = $\lambda e^{-\lambda x}$ 

![Exponential PDF](https://upload.wikimedia.org/wikipedia/commons/thumb/e/ec/Exponential_pdf.svg/400px-Exponential_pdf.svg.png)
- Graphs as smooth curves, density plots, or probability density functions.
- No gaps between values due to continuous nature.
- **Expectation (Mean):** The expected value of an exponentially-distributed random variable $X$ is $E[X] = \frac{1}{\lambda}$.

---

## Finding Expectation Using Moment Generating Function

**Moment Generating Function of Poisson Distribution**

The Poisson distribution is a discrete probability distribution that describes the number of events that occur in a fixed interval of time or space, given a constant average rate of occurrence $\lambda$.

The probability mass function (PMF) of the Poisson distribution is given by:

$P(X = k)$ = $\frac{e^{-\lambda} \cdot \lambda^k}{k!}$

Where:
- $X$ is a random variable following the Poisson distribution.
- $k$ is a non-negative integer representing the number of events.
- $\lambda$ is the average rate of events.

The moment-generating function (MGF) is defined as:

 $M(t)$ = $E(e^{tX})$ 

Where $E$ represents the expectation.

To find the MGF of the Poisson distribution, we'll use the PMF:

$M(t)$ = $E(e^{tX})$ = $\sum [e^{tk} \cdot P(X = k)$

Substituting the Poisson PMF:

$M(t)$ = $\sum \left[ \frac{e^{t\lambda} \cdot \lambda^k \cdot e^{-\lambda}}{k!} \right]$

$M(t)$ = $e^{t\lambda} \cdot e^{-\lambda} \cdot \sum \left[ \frac{\lambda^k}{k!} \right]$

The sum is actually the Taylor series expansion of   $e^\lambda$, so the MGF simplifies to:

$M(t)$ = $e^{\lambda \cdot (e^t - 1)}$

This is the moment-generating function of the Poisson distribution.

As mentioned, the moment generating function (MGF) of the Poisson distribution is $M(t) = e^{\lambda \cdot (e^t - 1)}$.

To find the expectation of a Poisson-distributed random variable $X$, we differentiate the MGF with respect to $t$ and then evaluate it at $t = 0$:

$E(X)$ = $\frac{d}{dt}$ $M(t)$ at $t=0$ 

Let's differentiate the MGF and evaluate it:

$M(t) = e^{\lambda \cdot (e^t - 1)}$

$\frac{d}{dt} M(t) = \lambda \cdot e^t \cdot e^{\lambda \cdot (e^t - 1)}$

Evaluate at $t = 0$:

$\frac{d}{dt}$ $M(t)$  = $\lambda \cdot e^0 \cdot e^{\lambda \cdot (e^0 - 1)}$ = $\lambda$

So, the expectation of a Poisson-distributed random variable $X$ is $E(X) = \lambda$.

---

### Exponential Distribution

---
**Moment Generating Function of Exponential Distribution**

The Exponential distribution is a continuous probability distribution that describes the time between events in a Poisson process, where events occur at a constant average rate ($\lambda$).

The probability density function (PDF) of the Exponential distribution is given by:

$f(x) = \lambda \cdot e^{-\lambda x}$

Where:
- $x$ is a non-negative continuous random variable representing the time between events.
-  $\lambda$ is the average rate of events.

The moment-generating function (MGF) is defined as before:

$M(t) = E(e^{tx})$

To find the MGF of the Exponential distribution, we'll use the PDF:

$M(t) = E(e^{tx}) = \int [e^{tx} \cdot \lambda \cdot e^{-\lambda x}] dx$

$M(t) = \lambda \cdot \int e^{(t-\lambda)x} dx$

$M(t) = \frac{\lambda}{\lambda - t}$

Recall that the moment generating function (MGF) of the Exponential distribution is $M(t)$ = $\frac{\lambda}{\lambda - t}$.

To find the expectation of an Exponential-distributed random variable $X$, we differentiate the MGF with respect to $t$ and then evaluate it at $t = 0$:

$E(X) = \frac{d}{dt}$ $M(t)$ at $t=0$


$M(t)$ = $\frac{\lambda}{\lambda - t}$

$\frac{d}{dt} M(t) = \frac{\lambda}{(\lambda - t)^2}$

Evaluate at $t = 0$:

$\frac{d}{dt}$ $M(t)$ = $\frac{\lambda}{(\lambda - 0)^2} = \frac{1}{\lambda}$

So, the expectation of an Exponential-distributed random variable $X$ is $E(X) = \frac{1}{\lambda}$.

---


In summary, discrete random variables have specific, separate values with associated probabilities, while continuous random variables can take on a continuous range of values and are described by probability density functions. The choice of distribution depends on the nature of the data and the problem at hand.<br><br>For the next post, I am going to elaborate on some examples of usage of Poisson and exponential distributions.


---

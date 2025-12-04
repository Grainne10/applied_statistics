# applied_statistics
Coursework for Applied Statistics - Data Analytics
**by Grainne Boyle**

![teaimage](img/tea.jpg)

**README Content:**

1. [Overview](README.md/#overview)
2. [Contents](README.md/#repository-contents)
3. [Problems](README.md/#tasks)

## Overview

I am a student at the [Atlantic Technological University](https://www.atu.ie/), Galway, studying the Higher Diploma in Science in Data Analytics on a part-time basis over 2 years. This repository contains my coursework for the Applied Statistics module, completed as part of the Winter 25/26 assessment.  
The purpose of the project is to demonstrate my understanding of statistical concepts by applying statistical methods, simulation techniques, and analytical workflows in Python. All work is presented in a Jupyter notebook, which includes clear explanations, commentary, and visualisations to support the statistical results.
The assessment covers four problems: Extending Fishers' Lady Tasting Tea experiment, sampling variability under the normal distribution, analysing type II error rates in t-tests, and comparing ANOVA with multiple pairwise tests.
The notebook is designed to present clear reasoning, well explained methods, and results that reflect both the statistical theory and what I’ve learned in the course.

## Contents

## Problems

### Problem 1 - Extending  the Lady Tasting Tea Experiment
This problem extends Fisher's *Lady Tasting Tea* experiment.  
In this experiment, the null hypothesis is that the lady cannot actually taste the difference and any correct answers are due to guessing. It is the idea that we assume to be true until evidence shows us that it is not.  We assume the null hypothesis is true unless the data provide strong evidence against it. When a result is statistically significant, it means the evidence is unlikely to be explained by chance alone, so we reject the null hypothesis.


In the original test, the probability of correctly identifying all 4 tea-first cups by chance is:

$$
P = \frac{1}{\binom{8}{4}} = \frac{1}{70} \approx 0.0143
$$

When the experiment is extended to 12 cups (8 tea-first, 4 milk-first), the number of possible combinations is:

$$
\binom{12}{8} = \frac{12!}{8!(12-8)!} = 495
$$

so the probability of guessing all 8 tea-first cups correctly is:

$$
P = \frac{1}{495} \approx 0.0020.
$$

This shows us it is much more difficult to get all cups right in the extended experiment.

To check the exact probability calculation, I simulated the experiment in Python using NumPy.
In the simulation, the cups were shuffled many times and the lady  “guessed” randomly each time. 
The simulation result matched the theoretical probability very closely, confirming our calculation. The computer experiment confirmed that our mathematical answer was correct.

Under the null hypothesis, the participant is only guessing and has no real ability to tell the difference between tea-first and milk-first cups. If this assumption is true, then getting all cups correct should be very unlikely. . In the extended 12-cup version, this chance becomes much smaller (0.2%) than in the original 8-cup version (1.43%). This means the extended experiment provides stronger evidence that a perfect score is not due to guesswork.

### Problem 2 - Normal Distribution

In this problem, I explored how the standard deviation behaves when sampling from a standard normal distribution. I generated 100,000 samples, each samples containing 10 values. For every sample, I computed two versions of the standard deviation, one using ddof=0 and one using ddof=1(delta degrees of freedom).I plotted the results on a histogram with transparency so that I  can visually compare their sampling distributions.

The results show that when the sample size is small(n=10), the ddof=0 estimator tends to underestimate the true standard deviation of the population. This shows dividing by n does not account for the fact that one degree of freedom is lost when the sample mean is calculated. In contrast , the ddof = 1 divides by n-1, producing slightly larger values on average. This is why its histogram is shifted slightly to the right, and its peak is closer to the true value of 1. This highlights that sample standard deviation ddof = 1 is unbiased and the ddof=0 is biased downward when the sample sizes are small.

To see how sample size affects these estimators , I repeated the simulation with samples of size 100. With the larger sample size, the two histograms overlapped more. Both estimators produced values tightly clustered around 1, and the difference between ddof=0 and ddof=1 were very small. This confirms that as the sample size increases, the impact of the ddof adjustment becomes smaller, and both estimators are closer to the true population standard deviation.

This problem shows our understanding of sampling distributions, bias in estimation and the role of degrees of freedom in statistics. It reinforces the empirical rule and shows how repeated sampling from a distribution behaves in practice.

 

[stats](img/statistics.jpg)
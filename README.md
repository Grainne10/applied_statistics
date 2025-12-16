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

### Problem 3 -  T-tests

In this problem, I explored how Type II error rates behave when performing an independent samples t-test under different true mean differences between two populations. 
The purpose of this problem is to investigate the relationship between effect size, statistical power, and Type II errors. It demonstrates how sensitive the t-test is to differences between two population means.

Two independent samples were repeatedly drawn, each group had a sample size of n =100 and the experiment was repeated 1000 times:
Group A was sampled from a standard normal distribution:
N(0,1)N(0, 1)N(0,1)
Group B was sampled from a normal distribution with the same variance but a shifted mean:
N(d,1)N(d, 1)N(d,1)
A two-sample independent t-test was performed for each simulation at a significance level of α=0.05\alpha = 0.05α=0.05. explain alpha
Null Hypothesis (H0H_0H0​):
There is no difference between the population means of Group A and Group B.
μA=μB\mu_A = \mu_BμA​=μB​
Hypothesis
The population means of Group A and Group B are different.
μA≠μB\mu_A \neq \mu_BμA​=μB​
When d=0d = 0d=0, both groups come from identical distributions and the null hypothesis is true. As ddd increases, the null hypothesis becomes false, and a real difference between the populations exists.

Type II Error Explanation:
A Type II error occurs when a hypothesis test fails to reject the null hypothesis even though it is false. This is also known as a false negative.   In this simulation, a Type II error happens when the t-test does not detect a real difference between the two population means when d>0d > 0d>0.
A real-world example of a Type II error would be a medical test that incorrectly indicates a patient does not have a disease when they actually do. The consequence is that the condition goes untreated. Similarly, in statistics, failing to detect a real effect can lead to incorrect conclusions and poor decision-making.

Results and Interpretation:
The table of results shows the estimated false negative rate for different values of the true mean difference ddd:
When d=0d = 0d=0, the null hypothesis is true, and the test correctly fails to reject it most of the time (about 94%).
For small values of ddd (e.g., 0.1 or 0.2), the false negative rate is still high. This means the t-test struggles to distinguish between the two populations when the difference is subtle.
As ddd increases, the false negative rate decreases rapidly.
For larger values of ddd (around 0.7 and above), the false negative rate approaches zero, indicating that the t-test almost always detects the real difference.
This behavior shows that the power of the t-test increases as the true effect size increases. Power is defined as 1−Type II error rate1 - \text{Type II error rate}1−Type II error rate, so lower false negative rates correspond to higher power.
The plot visualizes the relationship between true mean difference (effect size ddd) and the Type II error rate. This  shows a steep decline in false negatives as ddd increases. When the populations are very similar, the test frequently misses the effect. As the populations become more separated, the test becomes more reliable.
This visualization reinforces the idea that statistical tests are not equally sensitive to all effect sizes. Detecting small effects requires larger sample sizes or more powerful testing strategies.

Conclusion

This problem demonstrates how Type II errors depend strongly on effect size and illustrates the practical limitations of hypothesis testing. While the t-test performs well for moderate to large differences, it can miss small but real effects. Understanding this tradeoff is essential in real-world applications such as scientific research, psychology, and medical testing, where failing to detect a true effect can have serious consequences.

# a Review and comment
### Problem 4 - ANOVA
 
----------------------------------------
END

![stats](img/statistics.jpg)
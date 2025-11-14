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
In this experiment, the null hypothesis is that the lady cannot actually taste the difference and any correct answers are due to guessing.


## Add a note on the null hypothesis
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

It is much more difficult to get all the cups right in the extended experiment.

To check the exact probability calculation, I simulated the experiment in Python using NumPy.
In the simulation, the cups were shuffled many times and the lady  “guessed” randomly each time. 
The simulation result was almost the same as the value we calculated using the formula. The computer experiment confirmed that our mathematical answer was correct.

The null hypothesis assumes that the participant is only guessing and has no real ability to tell the difference between tea-first and milk-first cups.
If this assumption is true, then getting all cups correct should be very unlikely. In the extended 12-cup version, this chance becomes much smaller than in the original 8-cup version. This means the extended experiment provides stronger evidence that her choices are not due to guesswork.






![statistics](img/statistics.jpg)
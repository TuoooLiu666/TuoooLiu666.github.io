---
layout: post
title: Statistics Notes
date: 2024-07-12 11:12:00-0400
description: Statistics notes
categories: Statistics
tags: Statistics DataScience
---


## Statistical analysis

- steps
  - Define hypothesis and plan research design
    - Define hypothesis
    - Research design
      - experimental design
        - directly influence variables
        - can assess a cause-and-effect relationship
      - correlational design
        - only measure variables
        - can explore relationships between variables
      - descriptive design
        - only measure variables
        - can study the characteristics of a population or phenomenon
  - Collect data from a sample
    - sampling type
      - probabilistic sampling for parametric testing
      - non-probabilistic sampling for non-parametric testing
    - create an appropriate sampling procedure
      - calculate sample size
        - significance level
        - statistcial power
        - expected effect size
  - Summarize data with descriptive statistics
    - data inspection
    - measure central tendency
    - measure variability
  - Test hypothesis or make estimates with inferential statistcis
    - point estimation
    - hypothesis testing
    - interval estimation
  - Interpret results and draw conclusions

### Experimental design

- experimental unit
  - the individual or group of individuals that are the subject of the experiment
- experimental variable
  - the variable that is manipulated by the experimenter
- control variable
  - the variable that is held constant by the experimenter
- independent variable
  - the variable that is manipulated by the experimenter
- dependent variable
  - the variable that is measured by the experimenter
- experimental group
  - the group of individuals that are exposed to the experimental variable
- control group


### Sampling

- calculate sample size
        - significance level
        - statistcial power
        - expected effect size
  
### Hypothesis testing

- one-group
  - z-test
  - t-test
- two-group
  - z-test
  - t-test
  - Welch's t-test
- three-group
  - one-way ANOVA
  - two-way ANOVA
  - ANCOVA
    - to determine if there is a statistically significant difference between three or more independent groups after accounting for one or more covariates.
    - The covariate(s) and the factor variable(s) are independent
    - The covariate(s) are continuous
    - Homogeneity of variance
    - Independence of observations
    - No extreme outliers
    - Normal distribution of the dependent variable in each group
  - MANOVA: multivariate analysis of variance
    - identical to ANOVA except it uses two or more response variables
    - one-way
    - two-way
  - MANCOVA: multivariate analysis of covariance

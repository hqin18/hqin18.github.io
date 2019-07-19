---
layout: post
title: Preparing Capital One Interview
---

Today is my 1 year working anniversary at current company. To celebrate, I decide to start prepare the interview of Data Scientists at Capital One. I interviewed with Capital One sometime in 2017. Unfortunately, my first attempt didn't work out. The interview typically consists of four steps: coding test, phone screen, data challenge and on-site interview. 

## Coding test

Hackerrank test. 4 questions, 2 hours. This round is not very hard. The questions are simpler than leetcode easy questions. 


## Phone screen

I failed the phone screen round last time. After spent some time searching around I found some useful posts: [yoyoinwanderland](https://yoyoinwanderland.github.io/Interview-Capital-One/) is a great summary of common ML/DS questions with answers, and [a medium post](https://medium.com/acing-ai/capital-one-data-science-interview-questions-b6263d8a3af6), a list of C1 frequently asked questions.

### Statistics + Linear Models
1. interpret ANOVA table

Shame on me of forgetting ANOVA already. [A quick recap on one way ANOVA](https://newonlinecourses.science.psu.edu/stat414/node/218/)

2. what is VIF in regression output

It is a measure of how much the variance of estimated regression coefficient bk is inflated by the existence of correlation among the predictor variables in the model.A VIF=1 means there is no correlation among the kth variable and the remaining predictor variables, and hence the variance of bk is not inflated at all. The general rule of thumb is that VIF exceeding 4 warrants further investigation, while VIF > 10 is a sign of strong multicollinearity that requiring correction. [Reference](https://newonlinecourses.science.psu.edu/stat501/node/347/)

3. what are L1 L2 regularization

In regression, L1 L2 are common method to penalize complex models.

L1=Lasso, adds absolute value of magnitude. It shrinks less important feature's coefficient to zero, thus works well for feature selection.

L2=Ridge, adds squared magnitude. Works well to avoid overfitting

[Reference](https://towardsdatascience.com/l1-and-l2-regularization-methods-ce25e7fc831c)


### ML+Feature Engineering

1. How to handle missing data

* Understand how many are missing and why they're missing. Data bug? systematic missing? random missing?
* Can consider removal if the missing is small and not skewed towards certain distribution
* If numerical data missing, can impute using mean/median/mode or distribution
* For categorical missing, should handle carefully. Maybe encode it into another category
* check missing correlation can help understand if multiple variable have missing values in a related fashion

2. How to hanlde outlier

* First, how to identify outlier
- plot
- assume a distribution and check for standard deviations
- model based check
- cluster and check
- use PCA to reduce to 2 dim and check

* how to deal with outliers
- some models are robust to outliers, such as tree based models
- try non-parametric test instead of parametric test
- use a more robust loss function. MSE is not robust to outliers
- maybe remove/cap/transform data (log transformation, scaling)



## Data Challenge


## On-site

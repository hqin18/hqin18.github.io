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
A good [Summary Material](https://yoyoinwanderland.github.io/Interview-Linear-Regression/)

1. interpret ANOVA table

Shame on me of forgetting ANOVA already. [A quick recap on one way ANOVA](https://newonlinecourses.science.psu.edu/stat414/node/218/)

2. what is VIF in regression output/How do you detect multicollinearity?

It is a measure of how much the variance of estimated regression coefficient bk is inflated by the existence of correlation among the predictor variables in the model.A VIF=1 means there is no correlation among the kth variable and the remaining predictor variables, and hence the variance of bk is not inflated at all. The general rule of thumb is that VIF exceeding 4 warrants further investigation, while VIF > 10 is a sign of strong multicollinearity that requiring correction. [Reference](https://newonlinecourses.science.psu.edu/stat501/node/347/)

3. what are L1 L2 regularization

In regression, L1 L2 are common method to penalize complex models.

L1=Lasso, adds absolute value of magnitude. It shrinks less important feature's coefficient to zero, thus works well for feature selection.

L2=Ridge, adds squared magnitude. Works well to avoid overfitting

[Reference](https://towardsdatascience.com/l1-and-l2-regularization-methods-ce25e7fc831c)



### ML+Feature Engineering

A good [Summary Material](https://yoyoinwanderland.github.io/Interview-Classification/)

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
- use a more robust loss function. MSE is not robust to outliers, MAE (mean absolute error) is more robust to outliers
- maybe remove/cap/transform data (log transformation, scaling)

3. Tell me about a ML algorithm

### MapReduce, Hadoop, Bigdata

1. What is Hadoop:
 - Ecosystem: an open souce software framework for storing large amount of data and running applications on clusters of hardware.
 - HDFS: hadoop distributed file system, a storage solution
2. What is MapReduce:
 - a core component of Hadoop
 - limitation: can only batch one job at a time
3. What is Spark:
 - an open-source large scale processing engine
 - an solution in hadoop eco-system

 - [Brief Intro](https://hci.stanford.edu/courses/cs448g/a2/files/map_reduce_tutorial.pdf)
 - [Very Helpful - Hadoop vs Spark vs MapReduce](http://www.metistream.com/comparing-hadoop-mapreduce-spark-flink-storm/)
 - [Top Hadoop questions & answers](https://www.datasciencecentral.com/profiles/blogs/top-11-hadoop-interview-questions-answers)

### Credit Modeling questions

1. What machine learning model will you use to classify fraudulent transactions on credit cards?
- Logistic regression
- Random forests
- Anomaly detection might be helpful because of the high unbalanced data that normally exists in those scenarios (KNN, K-means, SVM)

2. Explain the various steps involved in the model building process
- read in the data: if too big, consider read in partitions or use other tools such as spark
- Exploratory data analysis(EDA): shape, dimension, data type, volume, fill in rate; define the problem - supervised learning? unsupervised learning? predictive modeling? clustering? correlation with response variable. check positive ratio to see if it's unbalanced.
- Data clean up: timestamp to date, shuffle, missing imputation (pandas, numpy), split into train/val/test sets
- learning curve: fit a series of simple models using different sizes of samples, report on performance, determine the proper size when model stopped improving
- algorithm selection: sensitive to use cases. predicting unseen data, don't use tree based models; huge amount of features, avoid svm as it's slow; avoid linear model when heavy collinearity presents
- feature selection: forward, backward, stepwise, importance, a lot other algorithms for model interpretability
- evaluation, auc for classification, confusion matrix when tpr/tnr are important;
- [Regression loss functions](https://heartbeat.fritz.ai/5-regression-loss-functions-all-machine-learners-should-know-4fb140e9d4b0)L1 loss is more robust to outliers, but its derivatives are not continuous, making it inefficient to find the solution. L2 loss is sensitive to outliers, but gives a more stable and closed form solution (by setting its derivative to 0.)
- [Classification loss functions](https://towardsdatascience.com/common-loss-functions-in-machine-learning-46af0ffc4d23)

3. How to set threshold for credit card fraud detection
- the default is 0.5; but need to observe confusion matrix to make a decision

4. what features would you use to determine credit risk given transaction history from the past two years
- Transaction amount
- Transaction count
- Transaction frequency
- Transaction recency
- Transaction by category: bar, hotel, grocery, etc.
- Transaction channel: credit card, debit card, wire transfer
- Distance between transaction address and billing address
- Fraud/Risk score
- Credit usage, max/min/average

A good reference of credit fraud prediction: 

[Part 1](https://songhuiming.github.io/pages/2018/05/05/credit-card-fraud-detection-imbalanced-data-modeling-part-i-logistic-regression/)

[Part 2](https://songhuiming.github.io/pages/2018/05/12/credit-card-fraud-detection-imbalanced-data-modeling-part-ii-random-forest/)

[Part 3](https://songhuiming.github.io/pages/2018/05/12/credit-card-fraud-detection-imbalanced-data-modeling-part-iii-ensemblingstacking-models/)

## Data Challenge


## On-site

How would you explain the multinomial distribution and write python code on a whiteboard to represent this distribution

1. Behavior questions:
- name a time you went above and beyond to help someone
- tell me about a time you sought out for someone else's expertise
- tell me about a time you persuade someone to implement a solution when they didn't think there was a problem
- what is your career plan
- Tell us a about a time when you worked effectively in a team environment

2. Break-even analysis

3. Tech interviews
- dynamic programming
- string manupulation
- backward induction on a multi-stage decision making problem
- map reduce (Explain a simple map reduce problem)
- probability questions (combination calculatoin, bayesian calculation, etc)

4. Read in a very large file of tab delimited numbers using python and count frequency of each number (don’t overthink this. Use python done in a few lines)

5. A/B test vs Multi-armed bandit
[Link](https://www.optimizely.com/optimization-glossary/multi-armed-bandit/)



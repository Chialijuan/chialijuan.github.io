---
layout: post
title: Difference between dev and test set
---
When curating our dataset for our ML experiments, the most straight forward way would be to curate a training set and a test set. However, usually in Deep Learning, there is always this dev set that people talk about. Even worse, sometimes people use the terms dev set and test set interchangably = MORE CONFUSION.

After reading several articles, I have come to conclude that:

* Dev set (aka validation set) is the sample dataset that is usually used to evaluate the models during hyperparameters tuning. 

```
E.g. to choose the no. of hidden units in a neural net, choose the best of 2 networks: training the network with 5, 10, 20 hidden units with maximum likelihood or training the network with 20 and 50 hidden units using early stopping)
```	
```
E.g. In Multinomial Naive Bayes, the `alpha` parameter is a hyperparameter and is usually tuned using `GridSearch` over potential parameter values and evaluated through cross-validation performed on the model at each parameter value
```

* Test set is the sample dataset where you evaluate your final tuned model on and compare it with other final models. 



---
layout: post
title: Structuring ML projects - Satisficing and Optimizing metric
---

Crafting a satisficing and optimizting metric could help you to craft the single number evaluation metric more easily.

Going back to our cat classifier example, say we are concern about the classification accuracy of our classifer, we could be using the F1-score as our measure of accuracy. And we are also concerned about the run time of our program (time taken to classify an image). Say we want the run time of our classifier to be less than 75s, anything more than that our users would get frustrated and not use our system. Given the 3 classifiers we have tested below, which should we choose? Perhaps one thing we could do is to combine accuracy and runtime into an overall evaluation metric such as a linear weighted sum of the 2 metric. 

|Classifier | Accuracy | Run time| Chosen|
|----|----|----|----|
|A| 90% | 10s||
|B| 92%| 40s||
|C | 95%| 100s|

However, something we could also do is to choose a classifier that maximizes accuracy subjected to the run time. In this case, we would say that accuracy is the optimizing metric because we want to maximize accuracy and the run time to be the satisficing metric. This is a reasonable way to trade off accuracy and run time.

In this case, we would choose classifier B as it gives the maximum accuracy with a runtime lesser than 75s. Hurray!

|Classifier | Accuracy | Run time| Chosen|
|----|----|----|----|
|A| 90% | 10s||
|B| 92%| 40s|We choose this!|
|C | 95%| 100s|

By doing so, you can focus majority of your efforts on optimizing that 1 important criteria and curb your efforts to improve the other metrices once their criterion are met.
 
More generally, if you have N things in your model that you care about, pick 1 that you care most about to be optimizing and the rest N-1 things to be satisficing. 

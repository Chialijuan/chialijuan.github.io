---
layout: post
title: Structuring ML projects - Single Number Evaluation metric
---

When tuning hyperparameters, trying out different learning algorithms or options for building our machine learning systems, you will find it fast if you have a *single number evaluation metric* to tell your if the new thing you are trying is performing better or worse than your previous idea. So before you embark on your ML project, it is always recommended that you establish a single real number evaluation metric for your problem. 

Applied ML is a very empirical process where you:

1. Have an idea  
2. Code it up  
3. Run the experiment to see the results then use the outcome of the experiment, to refine your ideas.

![_config.yml](https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcSJ8pNxennVWIUxXZlJYNb4p5eo_gIfVkBC_AODNHRDl8FdjyV8mA)

This loop continues to keep improving your algorithm.

Here's an example: 

Say you have a cat classifer A, by changing the hyperparameters and training sets or so, you have trained a new cat classifier B. Perhaps you would like to evaluate their performance by looking at their precision and recall(would write a future post on this).

Let's say that the performance of the 2 classifiers are as such:

|  Classifier  | Precision | Recall |
| -------- |-----| -----|
| Classifier A   | 95% | 90% |
| Classifier B  | 98%   |  85%|

Classifier A has 95% precision means that when classifier A says something is a cat, there is a 95% chance that it really is a cat. And having 90% recall means that of all the images in, say, dev set that are cats, classifier A could accurately retrieve 90% of them. 

Here, we see that there is often a trade off between precision and recall.  
You want:  
1. When the classifier says something is a cat, there should be a high chance it is a cat.
2. If all the images fed to the classifiers are cats, you want to retrieve a large portion of them as cats.

The problem here is, with classifier A doing better on recall and classifier B doing better on precision, which classifier is better then?  
![_config.yml](https://vignette.wikia.nocookie.net/rickandmorty/images/2/2e/S2e2_confused_jerry.png/revision/latest/scale-to-width-down/320?cb=20160919232226)  
_Confused Jerry is confused..._

With 2 evaluation metrics, precision **and** recall, it is difficult to quickly choose 1 out of 2 or 1 out of 10 classifiers. 

So instead of using 2 numbers, precision and recall to pick classifiers, find a new evaluation metric that combines the both. 

The standard way by ML practitioners to combine these 2 scores is called an F1-score, also the harmonic mean of precision and recall. 

![_config.yml](/images/PnR.png)

Calculating our F1-score we have...  

|  Classifier  | Precision | Recall | F1 Score
| -------- |-----| -----| ---- |
| Classifier A   | 95% | 90% | 92.4%|
| Classifier B  | 98%   |  85%| 91.0%|

With a single number evaluation metric, F1-score, we can see very clearly now that classifier A is better than classifier B!

Having a single number evaluation metric and properly curated development set help us to speed up the iterative process of improving our ML algorithm drastically. 

Note: Not all precision and recall problems should utilize the F1-score.There could be scenarios where you would favour precision over recall, vice versa. For instance, let's say you are getting your cat images by scraping pet websites. This data is unlabelled and too huge to be manually labelled. In such cases, you might not be able to know the true recall. A possible approach would be to optimize for precision instead of trying to evaluate the model based on the F1-score.




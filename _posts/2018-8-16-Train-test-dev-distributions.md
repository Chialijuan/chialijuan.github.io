---
layout: post
title: Structuring ML projects - Train, test, dev distributions
---

Curating the train, test and dev set for your ML project is crucial in the evaluation of your algorithm. The dev set, also called development set, is also sometimes called the hold-out cross validation set. Usually a train + test set would suffice for a simple classifier. However, building more complex models would require you to deal with hyperparameters which we could use the dev set to tune. We shall leave the workings for that to a later time. In this article, let's go through how to set up our train, test and dev set.

Going back to our cat classifier example, say you are planning to launch this app worldwide. So you could be looking at the U.S, U.K, South east asia, India, China, South America. How should you set up your datasets?

Perhaps you could split it in this way:

|Regions | Datasets|
|-----|----|
|U.S| Test|
|U.K| Test|
|South east asia| Dev|
|India| Dev|
|China | Dev|
|South america| Dev|

Turns out, this is a reaaalllly bad idea. Doing so would give you dev and test sets from different distributions. It is recommended that your dev and test set come from the same distribution. Here's why so: 

Picture your dev set and single number evaluation metric as a target board and the bull's eye is where you want to aim at. Using this target board speeds up the iteration of trying different ideas, experiment and evaluating the performance of each idea. So let's say you have found the right technique that is just inches away from the bull's eye after several months of hard work. And then you try to test this technique on the test set. Only to realize that the technique is not working well on the test set.

![config.yml](https://media.giphy.com/media/3o6MbtCPDaE3KSSrN6/giphy.gif)

WHY???

The problem is the way that we've set up the test and dev sets. By fine-tuning the technique on the 4 regions, we have overfitted to them.

Doing this is equivalent to working on the target for several months, only to change you mind and decided to shift the target board somewhere else. 

Why would you do that! 

To prevent being thrashed by flying pans from either your team or by youself, it is recommened instead to randomly shufle the data into the dev and test sets so that the distribution of the dev and test sets will come from the same distributions.

Choose a dev set and test set that reflects the data you expect would be important and you would be getting in the future to minimize hair-pulling moments. By setting your dev and test set to the same distribution, you would be really hitting the target you want.

Of course, the distribution of your training set would also affect the performance of your technique, which we would discuss about in the next article.

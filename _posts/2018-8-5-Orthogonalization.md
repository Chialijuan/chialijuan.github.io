---
layout: post
title: Structuring ML projects - Orthogonalization
---

This series is a summary based on the deeplearning.ai courses by Andrew Ng with a sprinkle of references from relevant blogs.

A challenge faced by many when embarking on machine learning projects is the lack of direction. In the vast ocean of algorithms, features, parameters, hyperparamets, evaluation metrices, it is easy to get lost without a good direction. Part 3 of the deeplearning.ai course aims to clear the fog surrounding junior ML practioners in an example-driven, assumptions-free video lectures. 

In this course, Andrew Ng explained that the process of **tuning the right stuff to try to achieve one effect** is called orthogonalization. 

Here's an example: 

![_config.yml](/images/TV_knobs.png)  

Imagine an old school television with lots of knobs that you could tune to adjust the display in different ways.
Perhaps there was one knob to adjust how tall/vertical the image would be, another to adjust how wide/horizontal it is, an another to adjust how much tilt, another to move the image to the left or to the right, etc.  

Assuming that the analog circuitry in the TV was done well, each knob should have 1 job: 1 knob to tilt the image, 1 knob to stretch image vertically, etc.

Imagine if the TV designers made a mistake, and you have a knob that tunes 0.1 x height of image, 0.3 x width of image, -0.5 x position of image on the horizontal axis. If you turn this knob, the height, width, position of the image all changes simultaneously. It would be almost impossible to tune the display into the center position! So in this context, orthogonalization refers to the TV designers had designed the knobs in such a way that each knob only does one thing/ This makes it much easier to tune the TV such that image gets centered to where you want it to be.

So how does this relate to machine learning?

For a supervised learning system to do well, you usually need to turn some knobs in the model to make sure that **four** requirements are met.  

1. You have to ensure that system is doing well on the training set    
This means that the performance on training set needs to pass some acceptability assessment.  

2. After doing well on the training set, you would want to do well on the dev set   

3. Next, you want to do well on the test set  

4. Finally, you hope it does well on in the real world which resolves into happy users :)  

In the TV tuning example, we want to have a single knob that adjusts the height of the image. So likewise, if our alforithm is not fitting well on the training set, we want a knob/ a set of knobs that can tune it to fit the training set well on the cost function. (eg. training on a bigger network, switch to better optimization algorithm like Adam)

So if the algorithm is not fitting well on the dev set, we want a separate set of knobs to tune it. The analogy here is you have tuned the width of your image on TV and now you want to tune the height of the image so you the knob for height. And you want to do this without affecting the width of the image too much. 

So perhaps a set of knobs around _regularization_ or getting a bigger training set to help the learning algorithm generalize better to the dev set could be used to tune to satisfy 2. To satisfy 3. the knob to tune would probably be getting a bigger dev set. Because doing well on the dev set but not test could means that you've overturned to your dev set. And finally, if its scenario 4., you might want to backtrack to change either the dev set or cost function. Because this could mean that either your dev test set distribution is not set correctly (e.g. different distribution) or your cost function isn't measuring the right thing.

*Tip:* early stopping is discouraged when traning a neural network as it affects >= 1 criteria. Stopping early might lead algorithm to fit training set less well, and it is also used to improve dev set performance. Early stopping is a less-orthogonalized knob which might make lives harder. 

Conclusion: Figure out exaclty what's wrong and have exactly one knob or a specific set of knob dedicated to that problem that is limiting the performance of the ML system.


References:
https://www.coursera.org/lecture/machine-learning-projects/orthogonalization-FRvQe

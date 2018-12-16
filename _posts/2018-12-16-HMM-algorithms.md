---
layout: post
title:  Bayesian Network - Hidden Markov Model algorithms
---

In this article, we look at the 3 main algorithms used in Hiddne Markov Models.

### Forward Algorithm

This algorihtm is usually used to calculate the _probability of a state at a certain time, given the history of evidence_ (belief state). This process is also usually known as **filtering**. Note that a belief state can be calculated at each time step, but doing this does not produce the most likely state sequence, but rather the most likely state at each time step, given the previous history.

In mathematical terms, the goal of forward algorithm is to compute the joint probability of <img src="https://latex.codecogs.com/gif.latex?p(x_{t},y_{1:t})" title="p(x_{t},y_{1:t})" />,  

where  

   <img src="https://latex.codecogs.com/gif.latex?x_{t}" title="x_{t}" /> = state x at time t  
    
and  

   <img src="https://latex.codecogs.com/gif.latex?y_{1:t}" title="y_{1:t}" /> = sum of observations y from 1 to time t. 
   
_The forward algorithm is mostly used in applications that need us to determine the **probability of being in a specific state** when **we know about the sequence of observations**._

### Viterbi Algorithm

This algorithm is usually used for _finding the most likely sequence of hidden states (Viterbi path) that results in a sequence of observed events__.

Consider a village where all villagers are either healthy or have a fever and only the village doctor can determine whether each has a fever. The doctor diagnoses fever by asking patients how they feel. The villagers may only answer that they feel normal, dizzy, or cold.

    obs = ('normal', 'cold', 'dizzy')
    states = ('Healthy', 'Fever')
    start_p = {'Healthy': 0.6, 'Fever': 0.4}
    trans_p = {
       'Healthy' : {'Healthy': 0.7, 'Fever': 0.3},
       'Fever' : {'Healthy': 0.4, 'Fever': 0.6}
       }
    emit_p = {
       'Healthy' : {'normal': 0.5, 'cold': 0.4, 'dizzy': 0.1},
       'Fever' : {'normal': 0.1, 'cold': 0.3, 'dizzy': 0.6}
       }

We can determine the sequence of states based on the sequence of observations here:
![](https://upload.wikimedia.org/wikipedia/commons/7/73/Viterbi_animated_demo.gif)

### Baum Welch Algorithm

This algorithm is used to _maximse the HMM's parameters (start probabilities, transition probabilities, emission probabilities)._ Bascially, it is used to for the training problem and it is also commonly known as the forward-backward algorithm.

Quoted from Stackoverflow:

  For each sequence in the training set of sequences.

  1. Calculate forward probabilities with the forward algorithm
  2. Calculate backward probabilities with the backward algorithm
  3. Calculate the contributions of the current sequence to the transitions of the model, calculate the contributions of the current sequence to the emission probabilities of the model.
  4. Calculate the new model parameters (start probabilities, transition probabilities, emission probabilities)
  5. Calculate the new log likelihood of the model
  6. Stop when the change in log likelihood is smaller than a given threshold or when a maximum number of iterations is passed.
  

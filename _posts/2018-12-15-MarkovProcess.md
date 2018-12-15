---
layout: post
title:  Bayesian Network - Markov Process
---

Here let's break down the jargons:

* Markov Process: 

  Any random process that satisfies the Markov Property is known as Markov Process.

* Markov Property (memoryless property):  

  A stochastic process (or a random process that is a collection of random variables which changes through time) if the probability of future states of the process depends only upon the present state, not on the sequence of states preceding it.

  Below are the four common Markov models used in different situations, depending on the whether every sequential state is observable or not and whether the system is to be adjusted based on the observation made:

  |                      | System state fully observable | System state partially observable            |
  |----------------------|-------------------------------|----------------------------------------------|
  | System is autonomous | Markov model (chain)          | Hidden Markov model                          |
  | System is controlled | Markov decision process       | Partially observable Markov decision process |

* Markov Model:

  A statistical model that follows the Markov process. 

  E.g. A board game which pieces move around on the board according to a die roll, Snakes and Ladders. If we're looking at the begining of player 1's turn (observing the present state), and wondering what the board will look like at the begining of the next player 2's turn (predicting the future state), it doesn't matter how the pieces arrived at their current position (what you see at begining of player 1's turn = past history of system). 

* Hidden Markov Model [HMM]:

  A Markov Model in which the system being modeled is assumed to be a Markov Process with hidden states (or unobserved) states.

  E.g. Consider 2 friends Alice and Bob who lives across the world (Singapore; London) but talks on the phone daily about their daily activities. 
  Bob is only interested in 3 activities: walking in the park, shopping and baking. The choice of which activity he choose is determined exclusively by the weather on the given day. Alice has no information about the weather at Bob's place but she has a general sensing of the weather there (e.g. London is usually rainy) and what Bob likes to do on average. She also belives that the weather operates as a discrete Markov model (e.g. probability of it raining tomorrow depends on the weather yesterday). Since Bob tells Alice about his activities, those are the observations.

  The parameters of the HMM can be represented in Python below:

  ```python

  states = ('Rainy', 'Sunny')

  observations = ('walk', 'shop', 'clean')

  start_probability = {'Rainy': 0.6, 'Sunny': 0.4}

  transition_probability = {
     'Rainy' : {'Rainy': 0.7, 'Sunny': 0.3},
     'Sunny' : {'Rainy': 0.4, 'Sunny': 0.6},
     }

  emission_probability = {
     'Rainy' : {'walk': 0.1, 'shop': 0.4, 'clean': 0.5},
     'Sunny' : {'walk': 0.6, 'shop': 0.3, 'clean': 0.1},
     }
  ```
  ![](https://upload.wikimedia.org/wikipedia/commons/thumb/4/43/HMMGraph.svg/400px-HMMGraph.svg.png)

When talking about HMM, there are generally 3 probllems to be considered:

1. Evaluation problem
  * What is the probability that a particular sequence of observations is produced by a specific model?
  * For evaluation problem, **forward algorithm** or **backward algorithm** is used. (Not forward-backward algorithm)
  
2. Decoding problem
  * Given a sequence of observations and a model, what is the most likely sequence of states that produced the sequence?
  * For decoding problem, **Viterbi algorithm** is used.  
    e.g.  Given that Alice had a sequence of observations (e.g. 3 days of Bob's activities in seq), Alice can find out the most likely sequence of weather at Bob's place over the past 3 days.
    
3. Training problem
  * Given a model and a sequences, find the model that best fits the data
  * For training problem, **Maximum Likelihood Estimation**, **Viterbi training** (Not Viterbi decoding) or **Baum Welch (forward-backward)** could be used.

* Markov decision process:

A Markov Model that includes an agent that makes decisions which would affect the evolution of the system over time.

E.g. Aeroplane chess, a board game where the pieces' position at the beginning of the next player's turn depends only on the current pieces' position, the current player's dice roll (the Markov chain aspect) and the current player's decision as to which pieces to move based on the dice roll (the decision process aspect).)

Note: Workings of the algorithms would be posted in future posts.

References :
* https://math.stackexchange.com/questions/22982/what-is-the-difference-between-all-types-of-markov-chains\
* https://stats.stackexchange.com/questions/31746/what-is-the-difference-between-the-forward-backward-and-viterbi-algorithms

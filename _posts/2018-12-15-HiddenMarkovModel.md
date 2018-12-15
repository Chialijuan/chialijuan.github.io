---
layout: post
title: Bayesian networks: Markov Process
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

* Hidden Markov Model:

A Markov Model in which the system being modeled is assumed to be a Markov Process with hidden states (or unobserved) states.

E.g. Consider 2 friends Alice and Bob who lives across the world (Singapore; London) but talks on the phone daily about their daily activities. 
Bob is only interested in 3 activities: walking in the park, shopping and baking. The choice of which activity he choose is determined exclusively by the weather on the given day. Alice has no information about the weather at Bob's place but she has a sensing: London is usually rainy. 

* Markov decision process:

A Markov Model that includes an agent that makes decisions which would affect the evolution of the system over time.

E.g. Aeroplane chess, a board game where the pieces' position at the beginning of the next player's turn depends only on the current pieces' position, the current player's dice roll (the Markov chain aspect) and the current player's decision as to which pieces to move based on the dice roll (the decision process aspect).)

References :
* https://math.stackexchange.com/questions/22982/what-is-the-difference-between-all-types-of-markov-chains

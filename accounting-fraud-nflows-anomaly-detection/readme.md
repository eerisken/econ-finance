## Anomaly Detection using Normalizing Flows ##

This project implements an anomaly detection system using a deep normalizing flow model. The core idea is to train a model to learn the probability distribution of "normal" data. Once trained, data points that are assigned a very low probability by the model are flagged as anomalies.

## Core Concepts & My Intuition ##
**The Goal: Learning a Probability Distribution**
The fundamental task is density estimation. We want to create a model that can take any data point x and compute its probability, p(x). Anomalies are simply the points the model finds highly improbable.

**Normalizing Flows: The Basic Mechanism**
Directly defining p(x) for complex data is intractable. A normalizing flow learns this distribution indirectly. It learns a complex, invertible transformation f that can morph a simple base distribution (like a standard Gaussian, where probabilities are easy to calculate) into the complex distribution of our data. By tracking how this transformation stretches and shrinks space (the Jacobian determinant), we can compute the exact probability of any data point x.

**My Intuition: Flows as Implicit Bayesian Networks**
This is where the connection to graphical models becomes clear. Any joint probability distribution can be factorized using the chain rule of probability, which is the mathematical foundation of a Bayesian Network:

p(x)=p(x1​)p(x2​∣x1​)p(x3​∣x1​,x2​)…p(xD​∣x1..D−1​)

The challenge is that the performance of this factorization heavily depends on choosing the correct ordering of features. Finding the optimal structure of the underlying graphical model for a dataset is an NP-hard problem. We often don't know the true causal relationships between our features.

This is where the normalizing flow provides a powerful, "black-box" solution:

A Single Coupling Layer Imposes an Order: A single MaskedAffineAutoregressiveTransform calculates the output features based on a fixed, arbitrary ordering. It's like assuming one specific, simple Bayesian Network structure. By itself, this is a weak assumption.

Random Permutations Unlock the True Structure: The power comes from stacking multiple layers and using RandomPermutation between them. Each time we shuffle the features, the next coupling layer is forced to learn a different factorization with a different conditional ordering.

By composing many of these layers, the model is no longer locked into one arbitrary dependency structure. Instead, the deep stack of (Permutation -> Transform) blocks collectively approximates the true, complex joint distribution. The model effectively learns a powerful factorization of the data's probability distribution without ever needing us to explicitly define the correct graphical model structure beforehand.



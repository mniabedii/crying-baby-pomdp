# Crying Baby POMDP

A from-scratch implementation of the classic **Crying Baby Partially Observable Markov Decision Process (POMDP)** in Python.

The project is implemented entirely in a Jupyter Notebook and focuses on understanding the mathematical foundations of POMDPs and their direct translation into code.

Rather than relying on existing POMDP or reinforcement learning libraries, the mathematical formulation, probability calculations, Bayesian belief updates, and decision-making process are derived and implemented from scratch.

## Overview

The notebook covers the main components of a POMDP:

* State, action, and observation spaces
* Transition and observation models
* Reward function
* Belief states
* Bayesian belief updates
* Environment simulation
* Agent-environment interaction
* Finite-horizon POMDP planning
* Recursive value-function evaluation

The implementation is written from scratch using Python and NumPy, without dedicated reinforcement learning or POMDP libraries.

The goal is not simply to implement a POMDP, but to derive and understand the mathematics behind each component before implementing it.

## Problem

The caregiver cannot directly observe whether the baby is **hungry** or **full**. Instead, the caregiver receives noisy observations indicating whether the baby is **crying** or **quiet**.

Based on its current belief about the baby's hidden state, the caregiver can choose between three actions:

* `Feed`
* `Sing`
* `Ignore`

The objective is to make good decisions while reasoning about the baby's hidden state under uncertainty.

The problem is modeled as a POMDP:

$$
M = (S,A,T,R,O,Z,\gamma)
$$

where:

* $S$: State space
* $A$: Action space
* $T$: Transition model
* $R$: Reward function
* $O$: Observation space
* $Z$: Observation model
* $ \gamma\ $: Discount factor

## Belief State

Since the true state of the baby is not directly observable, the agent maintains a **belief state**: a probability distribution over the possible states.

$$
b_t(s) = P(s_t=s \mid h_t)
$$

where $h_t$ represents the history of previous observations and actions.

After taking an action and receiving a new observation, the agent updates its belief using Bayesian inference.

This allows the POMDP to be viewed as a fully observable decision problem over belief states.

## Decision Making

The agent uses a **finite-horizon POMDP value function** to select actions:

$$
V_h(b)=
\max_a
\left[
R(b,a)
+
\gamma
\sum_o
P(o\mid b,a)
V_{h-1}(b^{a,o})
\right]
$$

where:

* $b$ is the current belief
* $R(b,a)$ is the expected immediate reward
* $P(o\mid b,a)$ is the probability of receiving observation $o$
* $b^{a,o}$ is the updated belief after taking action $a$ and receiving observation $o$
* $h$ is the planning horizon
* $\gamma$ is the discount factor

The value function recursively evaluates possible future observations and beliefs before selecting the action with the highest expected value.

## Simulation

The environment maintains the baby's true state, while the agent only has access to its belief and the observations it receives.

The interaction follows:

```text
Agent
  │
  │ action
  ▼
Environment
  │
  ├── reward
  └── observation
  │
  ▼
Agent
  │
  └── update belief
```

The true state remains hidden from the agent, preserving the partial observability of the problem.

## Purpose & Acknowledgment

This project was inspired by Robert Moss's **Decision Making Under Uncertainty** course and its Crying Baby POMDP example implemented using the Julia POMDPs.jl ecosystem.

The original example is implemented in Julia. This project reimplements the three-action Crying Baby formulation in Python as an educational exercise while studying POMDPs and reinforcement learning.

### References

* [Decision Making Under Uncertainty — JuliaAcademy](https://github.com/JuliaAcademy/Decision-Making-Under-Uncertainty)
* [POMDP Lecture Notebook — Crying Baby](https://github.com/JuliaAcademy/Decision-Making-Under-Uncertainty/blob/master/notebooks/2-POMDPs.jl)
* [YouTube Lecture](https://www.youtube.com/watch?v=KDFzObtE6cs&t=119s)

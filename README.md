# Crying Baby POMDP

A simple implementation of the classic **Crying Baby Partially Observable Markov Decision Process (POMDP)** in Python.

The project is built entirely inside a Jupyter Notebook and focuses on understanding the main components of a POMDP through both mathematical explanation and code.

The notebook covers:

* state, action, and observation spaces,
* transition and observation models,
* reward function,
* belief states and Bayesian belief updates,
* environment simulation,
* and decision-making under partial observability.

The implementation is written from scratch using Python's standard library, without dedicated reinforcement learning or POMDP libraries. 

## Problem

The caregiver cannot directly observe whether the baby is **hungry** or **full**. Instead, they observe whether the baby is **crying** or **quiet** and can choose between three actions:

* `Feed`
* `Sing`
* `Ignore`

The goal is to make good decisions while reasoning about the baby's hidden state under uncertainty.

## Purpose & Acknowledgment

This project was inspired by Robert Moss's **Decision Making Under Uncertainty** course and its Crying Baby POMDP example implemented using the Julia POMDPs.jl ecosystem.

The original implementation is written in Julia. This project reimplements the the three-action Crying Baby formulation in Python as an educational exercise while studying POMDPs and reinforcement learning.

- [Decision Making Under Uncertainty — JuliaAcademy](https://github.com/JuliaAcademy/Decision-Making-Under-Uncertainty)
- [POMDP Lecture Notebook — Crying Baby](https://github.com/JuliaAcademy/Decision-Making-Under-Uncertainty/blob/master/notebooks/2-POMDPs.jl)
- [YouTube Lecture](https://www.youtube.com/watch?v=KDFzObtE6cs&t=119s)

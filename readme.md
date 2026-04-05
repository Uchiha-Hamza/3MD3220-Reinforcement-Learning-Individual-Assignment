# Reinforcement Learning on Tiny Flappy Bird

This project compares two reinforcement learning approaches on a simplified **Tiny Flappy Bird (TFB)** environment:

- **Monte Carlo control**
- **Sarsa($\lambda$)**

The goal is to study how both agents learn, how sensitive they are to hyperparameters, how they generalize across level configurations, and what their limitations are when moving from a simplified environment toward the original Flappy Bird setting.

## Project overview

The repository contains:

- implementation of the two RL agents
- training and evaluation pipeline
- parameter sweep experiments
- generalization experiments across multiple TFB configurations
- visualizations of learning curves, evaluation performance, value functions, and greedy policies
- the report written for the assignment

The main comparison focuses on:

- convergence speed
- reward and score achieved during training
- sensitivity to parameters
- robustness across environment settings
- interpretability of learned value functions and policies

## Algorithms

### Monte Carlo control
Monte Carlo learns from complete episodes by updating action values using the observed return after an episode ends.

Main characteristics:

- simple and stable to implement
- does not bootstrap
- updates only after full episodes
- can be slower to propagate useful information

### Sarsa($\lambda$)
Sarsa($\lambda$) is an on-policy temporal-difference method with eligibility traces.

Main characteristics:

- bootstraps from intermediate estimates
- updates online during episodes
- usually learns faster
- more sensitive to hyperparameters such as $\alpha$, $\epsilon$, and $\lambda$

## Environment

The experiments are conducted on a simplified **Tiny Flappy Bird** environment where the state is discretized using features such as:

- horizontal distance to the next pipe gap
- vertical offset from the center of the gap

The action space is binary:

- `idle`
- `flap`

This simplified environment makes tabular RL feasible and allows direct visualization of learned value functions and policies.

## Main results

The experiments show that:

- **Sarsa($\lambda)** generally learns faster than Monte Carlo
- Sarsa($\lambda) achieves higher training returns and evaluation scores
- Monte Carlo is more conservative and usually converges to weaker policies
- performance strongly depends on the hyperparameter choice, especially for Sarsa($\lambda)
- agents trained on one configuration may lose a lot of performance on different level settings
- the simplified TFB environment is useful for analysis, but it does not capture all the complexity of the original Flappy Bird game

# Reinforcement Learning on Text Flappy Bird

This repository contains my individual project for **3MD3220 Reinforcement Learning**.  
The goal is to compare two tabular reinforcement learning methods on **Text Flappy Bird**:

- **constant-** $\alpha$ **first-visit Monte Carlo control**
- **Sarsa($\lambda$) with replacing eligibility traces**

The project studies their learning behavior, final performance, parameter sensitivity, learned value functions, and ability to generalize to new level configurations.

---

## Project objective

The purpose of this project is to answer the following questions:

1. What experimental setup was implemented?
2. How do Monte Carlo and Sarsa($\lambda$) differ in convergence speed, rewards, scores, and sensitivity to hyperparameters?
3. How do the two Text Flappy Bird environments differ?
4. Can the same agents be applied to the original Flappy Bird setting?
5. How well does an agent trained on one level configuration transfer to another?
6. What do the results reveal about the strengths and limits of tabular RL in this task?

---

## Main result

The main conclusion is clear:

> **Sarsa($\lambda$) consistently outperforms Monte Carlo** on the compact Text Flappy Bird environment.

Compared with Monte Carlo, Sarsa($\lambda$):

- learns faster
- reaches much higher training return and score
- produces much stronger greedy evaluation performance
- learns a cleaner and more structured policy over the discretized state space

Monte Carlo still learns a meaningful policy, but it remains slower and significantly weaker overall.

---

## Environments

Two environment variants are considered:

### `TextFlappyBird-v0`
This is the main environment used in the experiments.  
It provides a compact low-dimensional state representation, making it suitable for **tabular reinforcement learning**.

### `TextFlappyBird-screen-v0`
This variant returns a screen-like observation.  
It is included to discuss why a raw board or pixel-style representation is a poor fit for a pure tabular approach.

---

## Methods

### Monte Carlo control
The Monte Carlo agent uses:

- first-visit updates
- constant step size $\alpha$
- epsilon-greedy exploration

It updates action-values only after a complete episode has finished.

### Sarsa($\lambda$)
The Sarsa($\lambda$) agent uses:

- on-policy temporal-difference learning
- replacing eligibility traces
- epsilon-greedy exploration

It updates action-values online during each episode and propagates reward information more quickly through traces.

---

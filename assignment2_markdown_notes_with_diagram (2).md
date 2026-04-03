# Technical Notes: Introduction to Monte Carlo Simulation for Structural Reliability

## Purpose of These Notes

The main objective of these notes is **summarizing** of how *Monte Carlo Simulation (MCS)* is used in structural reliability analysis. These notes are written as **technical study notes** for engineering students who want to understand the basic idea, and practical use of MCS.

The notes cover:

- the meaning of structural reliability
- the idea of a *limit-state function*
- the basic steps of Monte Carlo Simulation
- simple equations used in reliability estimation
- a short Python example for practice

---

## Why This Topic Matters

In engineering, structures are designed to stay safe under uncertain conditions. There are many factors in the calculation of risk estimating which are material strength, loads, dimensions, and environmental effects may all vary. Because of this uncertainty, engineers need to estimate the chance of failure.

---

## Key Terms

- **Reliability**: the probability that a structure performs safely under given conditions.
- **Failure probability** (*Pf*): the probability that the structure does not meet the required performance.
- **Limit-state function**: a function used to separate the *safe* condition from the *failure* condition.
- **Random variable**: a value that can change due to uncertainty, such as resistance or load.

---

## Basic Reliability Model

A simple reliability model can be written as:

`g(X) = R - S`

Where:

| Symbol | Meaning |
| --- | --- |
| `R` | Resistance or strength of the structure |
| `S` | Load effect or demand on the structure |
| `g(X)` | Limit-state function |

Condition:

- when `g(X) > 0`, the system is **safe**
- when `g(X) = 0`, the system is at the **limit state**
- when `g(X) < 0`, the system is in **failure**

---

## Main Idea of Monte Carlo Simulation

Monte Carlo Simulation estimates failure probability by generating many random samples of the uncertain variables and checking whether failure occurs.



## Simple Diagram

```text
Random variables (R, S)
        ↓
Generate many samples
        ↓
Compute g(X) = R - S
        ↓
Check whether g(X) < 0
        ↓
Estimate failure probability Pf
```

### Step-by-Step Workflow

1. Define the random variables, such as `R` and `S`.
2. Assign a probability distribution to each variable.
3. Generate many random samples.
4. Calculate the limit-state value `g(X)` for each sample.
5. Count how many samples give `g(X) < 0`.
6. Estimate the failure probability.

The basic estimate is:

`Pf ≈ Nf / N`

Where:

- `Nf` = number of failure samples
- `N` = total number of simulations

---

## Example

Assume that:

- `R` follows a normal distribution with mean `100` and standard deviation `10`
- `S` follows a normal distribution with mean `80` and standard deviation `15`

For each simulation:

1. randomly generate one value of `R`
2. randomly generate one value of `S`
3. compute `g = R - S`
4. record failure when `g < 0`

The ratio of failures gives an estimate of the probability of failure.

---

## Notes 

- A **larger number of simulations** usually gives a more stable estimate.
- A **smaller failure probability** means the system is more reliable.
- Monte Carlo Simulation is easy to understand, but it may take more computation time when failure is very rare.
- MCS's result can be used for comparing with other methods such as *FOSM* or *FORM*.

---

## Example Python Code

```python
import numpy as np

N = 100000
mu_R, sigma_R = 100, 10
mu_S, sigma_S = 80, 15

R = np.random.normal(mu_R, sigma_R, N)
S = np.random.normal(mu_S, sigma_S, N)

g = R - S
failures = np.sum(g < 0)

Pf = failures / N
print("Estimated failure probability =", Pf)
```

This code shows the method of estimating failure probability using random sampling.

---

## Advantages and Limitations

### Advantages

- simple to understand
- flexible for complex problems
- useful when analytical solutions are difficult

### Disadvantages

- may require a large number of simulations
- can be slow when failure happens very rarely
- result accuracy depends on model 

---

## Useful Resources

- [Markdown Guide](https://www.markdownguide.org/)

---

## Summary

These notes conclude that **Monte Carlo Simulation** is a method for estimating structural failure probability under uncertainty. By doing this step by step, defining random variables, generating many samples, and checking the limit-state function. Engineers can evaluate failure probability using MCs whether a system is safe or not. This makes MCS a tool in *scientific and technical note-taking* for reliability and risk assessment in engineering topics.

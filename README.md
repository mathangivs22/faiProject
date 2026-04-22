# faiProject
# Reproduction of "Learning to Predict by the Methods of Temporal Differences"
### Richard S. Sutton (1988)

---

## Overview
This project is a reproduction of Sutton's 1988 foundational paper on Temporal Difference (TD) learning. The paper introduces TD(λ), a class of incremental learning procedures that update predictions based on the difference between consecutive estimates over time, without waiting for a final outcome. This reproduction validates the core claims of the paper through implementation and experimentation on the bounded random walk environment.

---

## Requirements
- Python 3
- NumPy
- Matplotlib

---

## How to Run
Open the notebook in Google Colab or Jupyter Notebook and run all cells sequentially.

---

## Environment
The experiments are conducted on the **bounded random walk** environment:
- **5-state version** — 5 non-terminal states, 2 terminal states, agent starts at middle state (State 3)
- **10-state version** — Extended environment to test scalability
- Reward of +1 at right terminal, 0 elsewhere
- Agent moves left or right with equal probability

---

## Parameters Used
| Parameter | Value |
|-----------|-------|
| Learning Rate (α) | 0.1 (varied from 0.01–0.5 in sensitivity experiment) |
| Discount Factor (γ) | 1.0 |
| Episodes | 100 (1000 for value estimation) |
| Independent Runs | 100 |
| Lambda (λ) | {0, 0.2, 0.4, 0.6, 0.8, 1.0} |

---

## Experiments & Graphs

### 1. RMS Error vs Episodes
Plots the average RMS error over 100 episodes for TD(0) at λ=0, TD(0.5) at λ=0.5, and Monte Carlo at λ=1.0, averaged across 100 runs. Shows the learning progression and convergence speed of each method.

### 2. TD(0) vs MC across Learning Rates
Plots the average RMS error across learning rates (α) ranging from 0.01 to 0.5 for TD(0) and Monte Carlo. Shows the sensitivity of each method to the choice of learning rate.

### 3. Performance Metrics Table
Reports four metrics — Final RMS Error, Convergence Episode, Total Error, and Standard Deviation — for each λ value across both 5-state and 10-state environments.

### 4. Value Estimation Comparison
Compares the learned state values of TD(0) and Monte Carlo against the analytically computed true values after long training (1000 episodes).

---

## Key Findings
- Intermediate values of λ (0.4–0.6) achieve the best balance between accuracy and efficiency
- TD(0) is the most stable method with the lowest standard deviation across runs
- Monte Carlo converges faster initially but is less accurate and stable in the long run
- TD(0) is more robust across a wider range of learning rates compared to Monte Carlo
- Optimal λ shifts higher as environment complexity increases from 5 to 10 states

---

## Reference
Sutton, R. S. (1988). Learning to predict by the methods of temporal differences. *Machine Learning*, 3(1), 9–44.

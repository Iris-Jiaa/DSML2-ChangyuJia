## Lab Log Week 10

**Dates:** March 17, 2026 to March 20, 2026

> **Experimental code**: [dsml-deepLearning.ipynb](../notebook/dsml-reinforcementLearning.ipynb)

### 1. Experiment Background and Data Source

Building on the supervised value network from Week 9, this experiment shifts to reinforcement learning. The same Kaggle chess dataset (FEN positions with black_score) is used for pretraining the value head, after which the agent improves via self‑play without relying on the provided “best_move” labels.

### 2. Problem Definition

The objective is to train an agent that learns optimal chess play purely through interaction. The agent must balance exploration and exploitation to maximize long‑term rewards (win/draw outcomes). This week focuses on implementing a self‑play loop with a policy‑value network and evaluating its performance against a random baseline.

### 3. Solution and Experimental Steps

Key steps include:

- **Environment & Reward Design**

- **Network Architecture**

- **Pretraining**

- **Self‑Play & PPO Update**

- **Evaluation**

### 4. Experimental Results and Key Findings

- **Pretraining Loss:** Loss decreased from 0.6910 (epoch 1) to 0.5009 (epoch 2), indicating the value network learned a reasonable mapping from board to normalized score.

- **Self‑Play Progress:**After 25 iterations, self‑play outcomes were mostly draws (9 draws, 1 black win). The agent’s win rate against random play was 0% at the last evaluation (iteration 25) and 18% in the final independent test, showing the agent is still in an early exploration phase.

- **Loss Trend:**The value loss continued to drop to ~0.47, confirming that the value predictions became more consistent with actual game outcomes over time.

### 5. Reflections

The transition from supervised learning to reinforcement learning introduces significant complexity. The current reward structure (sparse + material) may not provide enough guidance for rapid early improvement. The high draw rate suggests the agent often reaches dead‑end positions or avoids decisive moves. Future work should refine reward shaping, increase self‑play games per iteration, and implement a full PPO policy loss to accelerate learning. Despite modest win rates, the value loss convergence indicates the network is absorbing useful information from self‑play.

Overall, this training process effectively validated the feasibility of the "pre-trained value head + self-play reinforcement learning" framework in training chess agents. The model possesses basic move capabilities, but further optimization is needed in areas such as model structure, exploration strategy, number of training rounds, and reward mechanism to improve its chess performance.
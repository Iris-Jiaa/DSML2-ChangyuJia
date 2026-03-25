## Lab Log Week 10

**Dates:** March 23, 2026 to March 26, 2026

> **Experimental code**: [dsml-deepLearning.ipynb](../notebook/dsml-reinforcementLearning.ipynb)

### 1. Experiment Background and Data Source

This week, I integrated the complete PPO algorithm (including policy pruning, entropy regularization, and multi-round mini-batch updates) to jointly optimize the policy network and value network. As before, we used the same Kaggle chess dataset (FEN games, including Black's score) to pre-train the value head. Additionally, we implemented DQN as a baseline for comparison.

### 2. Problem Definition

The goal is to train a chess agent capable of making rational moves using reinforcement learning. The full PPO algorithm promises to be more efficient than the simplified version, leveraging a pre-trained value network and self-play to improve both policy and value. The agent's performance is evaluated by playing against random opponents, and the results are compared to a DQN agent with the same training budget.

### 3. Solution and Experimental Steps

Key steps include:

- **PPO Update**

- **DQN Baseline**

- **Comparison**

### 4. Experimental Results and Key Findings

- **Pretraining Loss:** Same as week 10 (0.691 → 0.501), providing a reasonable value estimate.

- **PPO Performance:**
    - Win rate against random peaked at 0.71 (iteration 10), confirming that full PPO can learn effective strategies.

    - Win rate later fluctuated but remained above DQN’s.

    - Loss decreased rapidly from ~0.6 to ~0.2 and stabilized around 0.1, indicating good convergence.

- **DQN Performance:**
    - Win rate stayed around 0.12 throughout, never exceeding 0.12.

    - Loss fluctuated between 0.3 and 0.5, showing limited improvement.

- **Comparison:**PPO substantially outperformed DQN under the same training budget, demonstrating the effectiveness of policy clipping and entropy regularization in large action spaces.

### 5. Reflections

The performance improved significantly after transitioning from the simplified PPO algorithm to the full algorithm: the win rate against random opponents jumped to 71%, demonstrating that joint policy-value optimization with appropriate regularization is crucial for chess learning. The value-based approach of the DQN algorithm has limitations in high-dimensional action spaces.

In summary, this experiment successfully validates that the full PPO algorithm with pre-trained value heads can learn meaningful chess strategies through a suitable amount of self-play.
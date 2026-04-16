## Lab Log Week 14

**Dates:** April 13, 2026 to April 17, 2026

> **Experimental code**: 
| Notebook | Topic | Models |
|----------|-------|--------|
| `dsml-classicAlgorithms.ipynb` | Wine Quality Classification | K-NN, K-Means, K-Medoids, SVM |
| `dsml-artificialNeuralNetworks.ipynb` | Fashion-MNIST Image Classification | MLP, CNN, ViT |
| `dsml-deepLearning.ipynb` | IMDB Sentiment Analysis | SimpleRNN, LSTM, Transformer |
| `dsml-reinforcementLearning.ipynb` | Chess Agent Training | PPO, DQN |


## Key Issues Found & Fixed

### Structural (all notebooks)

- Missing Table of Contents with anchor links
- Missing Work Log (CA requirement)
- Missing student name/ID comment in all import cells
- Missing or incomplete References sections
- Section headers lacking anchor IDs, breaking TOC navigation

### Logic & Ordering

- **classicAlgorithms:** `scaler.fit_transform(X_test)` → `scaler.transform(X_test)` — data leakage bug
- **ANN:** 8 cells in wrong order (analysis placed before the plots it analysed); 8 redundant cells deleted
- **ANN:** MLP Training Analysis referenced wrong accuracy values (87.48% → 87.85%); model comparison table similarly corrected
- **deepLearning:** `rnn_callbacks`, `lstm_callbacks`, `transformer_callbacks` referenced but never defined — NameError on run
- **deepLearning:** `import numpy as np` missing from imports despite `np` being used in 6 places
- **deepLearning:** Comparison table `.get('precision', 0)` always returned 0 due to dynamic metric key naming
- **reinforcementLearning:** `pretrain_value_head` function definition duplicated on one line (SyntaxError)
- **reinforcementLearning:** `train_agent` discarded the trained agent; demo cell used a fresh untrained `PPOAgent()` instead
- **reinforcementLearning:** `play_against_agent` called `get_action_probs` without unpacking the tuple return value

### Content Quality

- All Chinese-language comments translated to English across RL and deep learning notebooks
- Introduction cells expanded in all 4 notebooks to include technology choice rationale and stated goals
- Post-result analysis text added where missing (exploration section in RL notebook had descriptions only before code, none after)
- Conclusion sections expanded from 1–2 sentences to structured findings with limitations

## Observation

The most recurring pattern across all notebooks was **analysis text written before training had run**, resulting in placeholder or copy-pasted numbers that no longer matched the actual outputs. A disciplined write-as-you-run approach — writing the analysis cell immediately after observing the output — would prevent this category of error entirely in future work.
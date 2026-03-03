## Lab Log Week 8

**Dates:** March 3, 2026 to March 6, 2026

> **Experimental code**: [dsml-deepLearning.ipynb](../notebook/dsml-deepLearning.ipynb)

### 1. Experiment Background and Data Source

This experiment continues from last week's sentiment classification task, using the same Kaggle IMDB movie review dataset (50,000 reviews, half positive and half negative). Last week, we used a simple RNN model, achieving an accuracy only slightly higher than random guessing (approximately 50.9%). This week, we'll introduce more advanced architectures: LSTM and Transformer, and explore how modern deep learning models can effectively handle natural language sequences.

### 2. Problem Definition

The goal is to accurately distinguish between positive and negative sentiment in movie ratings. This experiment will not only evaluate the absolute performance of LSTM and Transformer, but also verify the advantages brought by the architectural evolution by comparing it with the results of RNN last week.

### 3. Solution and Experimental Steps

Key steps include:

- **Model Construction and Training:**
  - **LSTM Model:** Embedding layer (128-dimensional) → SpatialDropout1D → Two LSTM layers (64 units → 32 units, with dropout) → Fully connected layer → Output layer (sigmoid function).
  - **Transformer Model:** Embedding layer → Two Transformer encoder layers (4-head attention mechanism, 64-dimensional encoder per layer, 128-dimensional feedforward network) → Global average pooling layer → Fully connected layer → Output layer (sigmoid function).

- **Evaluation and Comparison:**
  - Calculate accuracy, precision, recall, and AUC on the test set.
  - Plot the training curve, confusion matrix, and ROC curve.
  - Make actual predictions on multiple new reviews and compare the outputs of the three models.

### 4. Experimental Results and Key Findings

The **RNN** performed no differently than random guessing (50.9% accuracy, AUC 0.500), failing to extract any effective sentiment features. The **LSTM** showed a slight improvement (54.6% accuracy), but it was still far from usable, indicating that standard LSTMs still struggle to capture complex semantic information in this task. On the other hand, the **Transformer** demonstrated comprehensive advantages: a stable learning process, a smooth validation curve, and no overfitting. Its high AUC (0.945) and clear confusion matrix indicate its strong classification ability. In specific sample tests, it was able to make accurate judgments with high confidence.

### 5. Reflections

For modern natural language processing tasks, Transformer-based architectures should be prioritized. Traditional RNN/LSTM models have proven insufficient for handling complex semantic information. Although the training time for Transformers is slightly longer (approximately 450 seconds, compared to approximately 320 seconds for LSTMs), the resulting performance improvement (nearly 32 percentage points higher accuracy) is entirely worthwhile.
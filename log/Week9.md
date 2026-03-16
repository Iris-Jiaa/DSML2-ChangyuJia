## Lab Log Week 9

**Dates:** March 10, 2026 to March 13, 2026

> **Experimental code**: [dsml-deepLearning.ipynb](../notebook/dsml-reinforcementLearning.ipynb)

### 1. Experiment Background and Data Source

This experiment aims to build and train a deep learning model for evaluating chess positions. The dataset comes from a Kaggle competition focused on chess AI, and includes FEN notation board states, corresponding pawn evaluation scores calculated from Black's perspective, and the best move for that position. This week, we will implement a neural network based on this exploratory data analysis.

### 2. Problem Definition

The core task is game evaluation: given a chessboard state represented in FEN format, the model must predict a scalar value representing White's advantage. Successfully modeling this complex mapping is crucial for building chess engines and move prediction systems.

### 3. Solution and Experimental Steps

Key steps include:

- **Data Encoding:**
  - This function converts the FEN string into a 12x8x8 tensor. These 12 channels represent the six piece types for both white and black pieces, thus creating a chessboard space and category representation suitable for convolutional neural networks.

- **Dataset Class:**
  - Load the CSV file using a custom PyTorch dataset class, calculate the white score based on the black score, and normalize the target score to a mean of zero and a variance of 1 to ensure training stability.

- **Neural Network Architecture:**A convolutional neural network (CNN) model specifically designed for 12-channel plate input.
  - **Convolutional block:** Three Conv2d layers (using BatchNorm2d and ReLU activation functions respectively) process the plate input, with the last layer using downsampling with a stride of 2, followed by an adaptive average pooling layer, outputting a fixed-size feature map.
  - **Fully connected block:** Flattens the features, passes them through a linear layer containing ReLU and Dropout, and outputs a scalar prediction.

- **Model Training:**The model is trained for 10 epochs using a standard regression setup (likely MSE loss). The training log shows the progressive decrease in average loss from 0.6785 to 0.1620, indicating that the model is effectively learning to approximate the board values.

### 4. Experimental Results and Key Findings

- **Loss Convergence:** The average loss decreased consistently over 10 epochs (0.6785 → 0.1620), demonstrating the model’s capacity to learn the regression task from the encoded board states.

- **Model Design Efficacy:**The use of a CNN with spatial inductive biases proved suitable for the grid-structured chess board, allowing the model to learn local piece patterns and their spatial relationships relevant for position evaluation.

### 5. Reflections

Data-centric learning. The performance of a model fundamentally depends on the quality and scope of the training data. The dataset contains many evenly matched positions, which may cause the model to predict draws. Future work could include targeted data collection or augmentation to cover more imbalanced and tactically rich positions.
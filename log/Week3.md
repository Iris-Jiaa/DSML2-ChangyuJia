## Lab Log Week 3

**Dates:** January 27, 2026 to January 31, 2026

> **Experimental code**: [dsml-artificialNeuralNetworks.ipynb](../notebook/dsml-artificialNeuralNetworks.ipynb)

### 1. Experiment Background and Data Source

This experiment was conducted in a Jupyter Notebook environment, using a Multilayer Perceptron (MLP) model to process image data. The goal is to perform multi-class image classification using a neural network.

The data comes from the publicly available Kaggle dataset: Fashion-MNIST, containing 60,000 training images and 10,000 test images, covering 10 fashion categories. Each image is a 28×28 pixel grayscale image with a label from 0 to 9.

### 2. Problem Definition

Predict the clothing category of fashion images.

This experiment aims to build and train a neural network to accurately classify these images. To facilitate model training, pixel values are normalized to the range [0,1].

### 3. Solution: Multilayer Perceptron (MLP) Model Experiment

Key steps include:

- **Data Preprocessing:** Load the data and normalize pixel values to the range [0,1].
- **Simple Perceptron Validation:** Implement a basic perceptron (without hidden layers) to validate forward propagation and initial predictions.
- **Data Augmentation:** Augment the training images (rotation, translation, scaling) using Keras' ImageDataGenerator to enhance the model's generalization ability.
- **Model Building:** Build a deeper neural network with two hidden layers (128 and 64 neurons respectively) and use ReLU activation and Dropout regularization to prevent overfitting.
- **Model Training and Evaluation:** Train the MLP model using the Adam optimizer and sparse classification cross-entropy loss function. Evaluate model performance on the validation and test sets.
- **Visualization and Analysis:** Plot the training history, generate a confusion matrix, and compare the original and augmented images.

### 4. Experimental Results

After 10 epochs of training, the MLP model achieved a test accuracy of approximately 88.19%. The training accuracy converged to approximately 88.20%, and the validation accuracy stabilized at around 88.15%–88.30%, indicating that the model did not exhibit significant overfitting.

**Key Findings:**

- The MLP model performed well on the Fashion-MNIST dataset, demonstrating the effectiveness of neural networks in image classification.
- Dropout regularization helps maintain consistency in performance between the training and validation sets.
- Data augmentation provides visual variations of images, which may help improve the model's robustness.
- The confusion matrix reveals some confusion between similar categories (e.g., shirts vs. T-shirts/tops), indicating areas for future improvement.

**Visual Analysis:** Training/validation accuracy and loss curves, confusion matrix, data augmentation comparison.

### 5. Reflections and Next Steps

The Multilayer Perceptron (MLP) model has proven to be a reliable baseline model for image classification. This experiment highlights the importance of normalization, regularization, and data augmentation in neural network training.

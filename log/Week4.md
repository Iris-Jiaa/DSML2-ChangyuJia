## Lab Log Week 3

**Dates:** February 2, 2026 to February 6, 2026

> **Experimental code**: [dsml-artificialNeuralNetworks.ipynb](../notebook/dsml-artificialNeuralNetworks.ipynb)

### 1. Experiment Background and Data Source

This experiment was conducted in a Jupyter Notebook environment, using a multilayer perceptron (MLP) and a convolutional neural network (CNN) to process image data. The goal was to utilize neural networks for multi-class image classification.

The data came from the publicly available Kaggle dataset Fashion-MNIST.

### 2. Problem Definition

Predict the clothing category in fashion images.

This experiment aims to build and train a convolutional neural network (CNN) to accurately classify these images. The experimental results will be compared and analyzed with those of a multilayer perceptron (MLP).

### 3. Solution: Convolutional Neural Network (CNN) Model Experiment

Key steps include:

- **CNN Model:** Build a convolutional neural network with:
  - **Convolutional Layers:** Two convolutional layers with 32 filters of size 3x3, each followed by a ReLU activation and max-pooling of size 2x2.
  - **Fully Connected Layers:** A flatten layer to convert the 2D feature maps into a 1D vector, and two dense layers with 128 and 64 neurons respectively, each followed by a ReLU activation and Dropout regularization (rate of 0.2).
  - **Output Layer:** A dense layer with 10 neurons (one for each class) and a softmax activation function.


- **Model Training:** Train model using the Adam optimizer and sparse categorical cross-entropy loss. The CNN is trained on augmented data using a generator.
- **Comparison and Analysis:** Evaluate both models on the test set, compare accuracy and loss, generate a confusion matrix for the CNN, and visualize the first-layer convolutional kernels to understand feature extraction.

### 4. Experimental Results and Key Findings

MLP model achieved a test accuracy of 88.20% (loss: 0.3231). CNN model achieved a test accuracy of 89.70% (loss: 0.2748), outperforming the MLP by 1.5 percentage points.

There is some confusion because shirts, T-shirts, jackets, and pullovers have similar overall shapes.

Convolutional kernel visualization: These eight convolutional kernels exhibit different weight distribution patterns; no two kernels are exactly alike, indicating that the model has learned multiple feature detectors. Notably, in many kernels, the absolute values ​​of negative weights are significantly larger than the absolute values ​​of positive weights.

These observations confirm that convolutional neural networks (CNNs) can successfully learn low-level features without any manual feature engineering, consistent with the theoretical advantages of convolutional architectures.

### 5. Reflections and Next Steps

We continued to apply the neural network concepts learned in class to datasets and highlighted the practical advantages of convolutional neural networks in image recognition.
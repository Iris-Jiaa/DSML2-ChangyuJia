## Lab Log Week 5

**Dates:** February 9, 2026 to February 13, 2026

> **Experimental code**: [dsml-artificialNeuralNetworks.ipynb](../notebook/dsml-artificialNeuralNetworks.ipynb)

### 1. Experiment Background and Data Source

This experiment extends previous research on Fashion-MNIST classification by introducing the Visual Transformer (ViT) model. While Convolutional Neural Networks (CNNs) dominate image recognition tasks, the Transformer architecture, originally designed for natural language processing, has been applied to the field of vision in recent years and has achieved state-of-the-art results on large-scale datasets. This experiment aims to evaluate the performance of ViT on a relatively small dataset (Fashion-MNIST) and compare it with the performance of Multilayer Perceptrons (MLPs) and CNNs.

This dataset remains a public dataset on Kaggle: Fashion-MNIST.

### 2. Problem Definition

This experiment uses a Vision Transformer to predict clothing categories in fashion images and compares its accuracy and loss with previously implemented Multilayer Perceptron (MLP) and Convolutional Neural Network (CNN) models.

This experiment aims to build and train a Vision Transformer (ViT) based on the Fashion-MNIST dataset, analyze its learning behavior, and identify the challenges of applying the transformer to small-scale image data.

### 3. Solution: Vision Transformer (ViT) Model Experiment

Key steps include:

- **ViT Model Architecture:**
  - **Patch Embedding:** Each 28×28 image is divided into non‑overlapping patches of size 7×7, resulting in (28/7)2=16(28/7)^2 =16 patches. Each patch is flattened and linearly projected to a 64‑dimensional embedding.
  - **Positional Encoding:** Learnable position embeddings are added to the patch embeddings to retain spatial information.
  - **Transformer Encoder:** Six identical transformer encoder layers are stacked. Each layer consists of:
    - **Layer normalization.** 
    - **Multi‑Head Self‑Attention.** 
    - **Residual connection.** 
    - **Another layer normalization followed by a multi‑layer perceptron (MLP) block with two dense layers (128 and 64 units) and GELU activation.** 
    - **Dropout (0.1) after attention and after the MLP.** 
- **Model Training:** The model employs the Adam optimizer (learning rate 1e-3) and a sparse classification cross-entropy loss function, and is trained for 20 epochs with a batch size of 64. It also uses the same data augmentation methods, early stopping mechanism, and adaptive learning rate decay strategy as CNNs to optimize the training process.
- **Comparison and Analysis:** Evaluate ViT on the test set and compare its accuracy and loss with previously trained MLPs and CNNs. Analyze how the model focuses on different image patches.

### 4. Experimental Results and Key Findings

The ViT model achieved a test accuracy of 80.04% (loss: 0.5330). The MLP and CNN models obtained 87.48% (loss: 0.3329) and 89.75% (loss: 0.2766) respectively. ViT underperformed compared to both traditional architectures.

Despite the lower performance, this experiment successfully demonstrated that the Visual Transformer (ViT) can be implemented and trained on small datasets, confirming the flexibility of the architecture.

### 5. Reflections and Next Steps

This exercise successfully demonstrates the application of the Transformer concept in computer vision and lays the foundation for exploring more advanced neural networks and deep learning models in future experiments.
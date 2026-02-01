# Lab Record

*Changyu Jia C00292876*

## Lab Log Week 1

**Date:** January 13, 2026 to January 16, 2026

> **Experimental code**: [dsml-classicAlgorithms.ipynb](../notebook/dsml-classicAlgorithms.ipynb)

### 1. Experimental Background and Data Source

This experiment was conducted using a Jupyter Notebook environment, based on processing data with the K-Nearest Neighbour (K-NN) model.

The data originates from the Wine Quality dataset (winequality-red.csv). This dataset contains 1,599 samples of red wine. The data is sourced from the UCI Machine Learning Repository, serving as a publicly available benchmark dataset.

### 2. Problem Definition

Predicting the quality score of red wine (a classification problem). The quality score is an integer, constituting a multi-class task. For simplification, the experiment binarizes the quality into "Low Quality" (score < 5) and "High Quality" (score > 6) to align with the binary classification setup in the code.The dataset features significant differences in feature scales, necessitating standardization.

### 3. Solution Method: K-NN Model Experiment

The main steps including:

- Data Preprocessing and Feature Standardization
- Model Training and Evaluation: Testing a range of K values, comparing accuracy and 5-fold cross-validation accuracy.
- Selecting the optimal K value and generating a confusion matrix and ROC curve for comprehensive model evaluation.
- Tools and Libraries: scikit-learn for modeling; matplotlib and seaborn for visualization.

### 4. Experimental Results

When K=1, the testing accuracy is highest (approximately 0.72), and the cross-validation accuracy is approximately 0.74.

Visualization Analysis: Accuracy Comparison Chart, Confusion Matrix, ROC Curve.

**Key Findings:** The K-NN model performs reasonably well in predicting wine quality, but feature engineering could potentially further improve performance.

### 5. Reflection and Next Steps

The K-NN model is simple and effective. The experiment highlighted the importance of standardization.

The plan for next week is to learn about other models and conduct a deeper analysis of feature importance.

# Lab Record

*Changyu Jia C00292876*

> **Experimental code**: [dsml-classicAlgorithms.ipynb](../notebook/dsml-classicAlgorithms.ipynb)

## Lab Log Week 2

**Date:** January 19, 2026 to January 22, 2026

### Experiment Log 1: K-Means-Based Cluster Analysis of Wine Quality Data

#### 1. Experimental Background

This experiment uses Python and the scikit-learn machine learning library to perform unsupervised learning analysis on a wine quality dataset. The core task is to use the K-Means clustering algorithm to explore the inherent clustering structure of the data, aiming to discover the potential categories of different wine samples.

#### 2. Problem Definition

The core problem of this experiment is how to determine the optimal number of clusters (k value). Choosing an inappropriate k value can lead to overfitting or underfitting of the clustering results, failing to effectively reveal the true structure of the data.

#### 3. Solution Method

A strategy combining the "elbow rule" and the "profile coefficient method" is adopted to scientifically determine the optimal k value.

Then, based on the determined k value, the K-Means algorithm is used for clustering. Simultaneously, for comparison, a K-Medoids model is also trained, and the silhouette coefficient is used as a unified evaluation metric for comparison.

#### 4. Experimental Results

- **Optimal k value determination:** The elbow rule curve shows a clear inflection point at k=3, suggesting an optimal cluster size of 3. The silhouette coefficient method achieves the highest score at k=2, but considering the intuitiveness of the elbow rule and subsequent analysis, the experiment ultimately adopted k=3.
- **Clustering effect visualization:** Dimensionality was reduced to 2 dimensions using PCA for visualization. The scatter plot shows that the data is not perfectly linearly separable.
- **Model comparison:**
    - K-Means (k=2): Silhouette coefficient = 0.202
    - K-Means (k=3): Silhouette coefficient = 0.161
    - K-Medoids (k=3): Silhouette coefficient = 0.134

K-Means (k=2) performs best on this metric, but K-Means (k=3) has advantages in business interpretability and visual separation.

#### 5. Reflection

The elbow rule and the profile coefficient method offer different suggested k values (3 vs 2). A comprehensive decision needs to be made considering domain-specific knowledge and the interpretability of the clustering results. K-Medoids performed slightly worse than K-Means on this dataset.

### Experiment Record 2: Wine Quality Classification Prediction Based on SVM

#### 1. Experimental Background

After completing the data clustering exploration, this experiment shifted to a supervised learning task. The goal was to build a classification model to predict the quality level of wine based on its physicochemical characteristics (in this experiment, wine was divided into "ordinary wine (0)" and "good wine (1)"). The powerful classification algorithm, Support Vector Machine (SVM), was chosen.

#### 2. Problem Definition

How to train a high-precision and robust SVM classifier to accurately distinguish between ordinary and high-quality wines? The key is to select the correct hyperparameters (kernel function, regularization parameter C, kernel coefficient gamma) for the SVM model to balance the model's complexity and generalization ability.

#### 3. Solution Method

A standardized process combining grid search and cross-validation was used for model optimization.

The quality scores were binary classified, and the features were standardized. The training and test sets were divided in a 7:3 ratio. Then, GridSearchCV was used to perform 5-fold cross-validation search on a defined parameter grid (C: [0.1, 1, 10, 100]; gamma: [1, 0.1, 0.01, 0.001]; kernel: ['rbf', 'linear']), with "accuracy" as the evaluation metric. Finally, the optimal model was evaluated on an independent test set, calculating accuracy, precision, recall, and F1 score, and plotting the confusion matrix and feature importance map.

#### 4. Experimental Results

- The optimal cross-validation score was 0.7417.
- The optimal model achieved an accuracy of 0.7562 on the test set. The classification report showed that the model's ability to identify the two classes was relatively balanced.
- **Result Visualization:** The number of false positives and false negatives in the confusion matrix were close. The absolute values of the coefficients in the linear SVM indicate that "volatile acidity" is the feature with the greatest impact on classification decisions. The accuracy of 5-fold cross-validation fluctuated between 0.68 and 0.80, with an average of 0.739, close to the accuracy on the test set, indicating that the model did not overfit.

#### 5. Reflection

The model achieved an accuracy of over 75% and demonstrated good generalization ability, making it a valid baseline model. The use of a linear kernel function with C=100 indicates that the data is approximately linearly separable, and the model focuses on reducing classification errors.

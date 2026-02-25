## Lab Log Week 7

**Dates:** February 23, 2026 to February 27, 2026

> **Experimental code**: [dsml-deepLearning.ipynb](../notebook/dsml-deepLearning.ipynb)

### 1. Experiment Background and Data Source

This week's experiment focuses on text sentiment classification using the IMDB movie review dataset from Kaggle. This dataset contains 50,000 reviews with positive or negative sentiment labels. The goal is to explore the features of the text data and implement a recurrent neural network (RNN) model for sentiment analysis.

This dataset remains a public dataset on Kaggle: Fashion-MNIST.

### 2. Problem Definition

This experiment aims to accurately classify the sentiment of comments as positive or negative based on their content. The core challenge lies in effectively extracting features from unstructured natural language text and building a model capable of understanding semantic and contextual sentiment. This involves a complete natural language processing workflow, including data exploration, text cleaning, feature representation, and the construction and optimization of the classification model.

### 3. Solution and Experimental Steps

Key steps include:

- **Data Exploration & Preprocessing:**
  - **Label Transformation:** Text labels (“positive”, “negative”) are mapped to numerical labels (1, 0).
  - **Text Statistical Analysis:** The length of the comment text is calculated. Results show an average length of approximately 231 words, a median of 173 words, a right-skewed distribution, and a small number of long-tail comments (the longest comment is 2470 words).
  - **Dataset Splitting:** The data is split into a training set (40,000 samples) and a test set (10,000 samples) in an 8:2 ratio to ensure consistent sentiment label distribution across the two datasets.
  -**Text Vectorization:** A vocabulary is constructed using a tokenizer. The original vocabulary contains 111,959 words. To balance efficiency and performance, the 10,000 most frequent words (coverage of 8.9%) are selected. All comments are converted into integer sequences and uniformly padded/truncated to a length of 200.
- **Model Building & Training:** The SimpleRNN model consists of an embedding layer, spatial dropout, two SimpleRNN layers, and a fully connected output layer.
- **Model Evaluation & Visualization:** The model achieved an accuracy of 0.5092 and an AUC of 0.5001, indicating performance close to random guessing. The classification report showed that the model had a higher recall rate for negative reviews (0.71) than for positive reviews (0.31).
-**Prediction Example:**The preprocessing process and the trained model are used to predict the sentiment of new comment texts and output the predicted sentiment (positive/negative) and its corresponding probability value.

### 4. Experimental Results and Key Findings

The initially constructed RNN model performed poorly on the test set, with an accuracy just above 50% and an AUC close to 0.5, indicating that the model failed to effectively learn effective patterns for distinguishing sentiment. The confusion matrix further revealed the problem of prediction imbalance.

### 5. Reflections and Next Steps

Try using more advanced architectures, such as bidirectional LSTM or attention-based models (Transformer), to better capture contextual information.
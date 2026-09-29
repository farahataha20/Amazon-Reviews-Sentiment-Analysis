 Amazon Reviews Sentiment Analysis — Deep Learning

Project Overview

This project builds a deep learning NLP pipeline for classifying Amazon customer reviews as Positive or Negative.

The goal is to analyze customer feedback and support product-development insights through automated sentiment classification.

Tech Stack

Python

TensorFlow / Keras

NLTK

NumPy

Pandas

Scikit-learn

Matplotlib

Seaborn

Optional: Google Cloud Natural Language API

Pipeline

Amazon Review
     ↓
NLTK Text Preprocessing
     ↓
Train-only Tokenizer
     ↓
Padding
     ↓
Embedding
     ↓
Bidirectional LSTM
     ↓
Dropout
     ↓
Sigmoid Output
     ↓
Positive / Negative Sentiment

Text Preprocessing

The notebook uses NLTK for:

Lowercasing

Punctuation removal

Stopword removal

Lemmatization using WordNetLemmatizer

Data Leakage Prevention

The dataset is split into:

80% Training

10% Validation

10% Test

The tokenizer is fitted only on the training text:

tokenizer.fit_on_texts(X_train_clean)

Validation and test data are transformed using the already-fitted tokenizer. This prevents information from the validation/test sets from influencing the learned vocabulary.

Sentiment Labels

The star rating is converted to binary sentiment:

1–2 stars → Negative (0)

4–5 stars → Positive (1)

3 stars → Neutral and removed

Model Architecture

The required deep learning architecture is:

Embedding
    ↓
Bidirectional(LSTM)
    ↓
Dropout
    ↓
Dense(1, activation="sigmoid")

The model is compiled using:

Optimizer: Adam

Loss: Binary Crossentropy

Metric: Accuracy

Early stopping is used based on validation loss.

Evaluation

The notebook includes:

Test accuracy

Classification report

Confusion matrix

Training vs validation accuracy

Training vs validation loss

Real-Time Prediction

A predict_sentiment() function is included to process a new review through the same preprocessing and tokenization pipeline and return:

Original review

Cleaned text

Predicted sentiment

Positive probability

Google Cloud NLP

The notebook includes a local simulation of the Google Cloud NLP integration concept.

The simulation identifies predefined product aspects such as:

Battery

Quality

Price

Delivery

Performance

Design

and associates them with the document sentiment.

Important

The simulation is not an actual Google Cloud API request.

An optional example for the official Google Cloud Natural Language client is included, but it is not executed because Google Cloud authentication credentials should not be stored directly in the notebook or repository.

How to Run on Kaggle

Create a new Kaggle Notebook.

Add the Amazon Reviews dataset as an input.

Upload/import amazon_reviews_sentiment_analysis_deep_learning.ipynb, or copy its cells into a Kaggle Notebook.

Make sure the dataset contains:

reviewText

overall

Run the cells from top to bottom.

GPU acceleration can be enabled in Kaggle for faster LSTM training.

Project Impact

The project demonstrates how customer feedback can be automatically classified to support faster understanding of customer sentiment and product-development decisions.

Files

amazon_reviews_sentiment_analysis_deep_learning.ipynb — Complete Kaggle-ready notebook

README.md — Project documentation

Notes

Model performance depends on the exact Amazon Reviews dataset, class balance, preprocessing choices, sequence length, and available compute resources. The notebook does not hard-code a specific accuracy because the result should be generated from the actual dataset used at runtime.

# Deep Learning-Based Stock Manipulation Classifier

This project is a deep learning system designed to automatically classify stock price time series as either "**pump-and-dump**" events or "**normal**" market behavior. The core of the system is an end-to-end machine learning pipeline built using Python and the PyTorch deep learning framework.

## 1. Synthetic Data Generation

The project overcomes the challenge of scarce real-world data by creating a large-scale synthetic dataset. This dataset contains a balanced mix of three distinct market behaviors:

    Pump-and-Dump: A sharp, artificial price increase followed by a rapid collapse.

    Mean-Reverting: Prices fluctuate around a stable average.

    Trending: Prices follow a consistent upward or downward drift.

Each synthetic time series is a self-contained, 252-day sequence. This process ensures the model learns to identify the manipulation pattern itself, independent of external market factors.

## 2. Model Architecture

The classifier is built on a Long Short-Term Memory (LSTM) network, a type of recurrent neural network (RNN) well-suited for time-series analysis. The model's architecture consists of:

    Two stacked LSTM layers to capture complex temporal dependencies in the price data.

    A dropout layer to prevent overfitting by randomly deactivating neurons during training.

    A final dense layer with a sigmoid activation function that outputs a single probability score, which is used to classify the entire sequence.

## 3. Training and Evaluation

The model is trained on the generated dataset and validated on a separate portion to ensure it generalizes well to new, unseen data. Key to the training process is early stopping, a technique that halts training when the model's performance on the validation set stops improving. This prevents the model from memorizing the training data. Finally, the model's performance is evaluated on a completely separate test set, using metrics like accuracy and a classification report to assess its ability to correctly identify the manipulated events.

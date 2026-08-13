# Fraud Detection Machine Learning Project

## Project Overview

This project builds a machine learning pipeline to detect fraudulent financial transactions using Python and scikit-learn. The goal was to address class imbalance and evaluate models using fraud-focused metrics.

## Dataset

The project uses the Credit Card Fraud Detection dataset containing 284,807 transactions with highly imbalanced fraud cases.

## Workflow

- Exploratory Data Analysis
- Class imbalance analysis
- Feature engineering
- SMOTE oversampling
- Model training
- Model evaluation
- Feature importance analysis

## Models Used

- Logistic Regression
- Random Forest

## Evaluation Metrics

Models were evaluated using:

- Precision
- Recall
- F1-score
- AUC-ROC

Accuracy was avoided as the primary metric because fraud datasets are heavily imbalanced.

## Tools Used

- Python
- Pandas
- NumPy
- Scikit-learn
- Imbalanced-learn
- Matplotlib
- Seaborn
- Jupyter Notebook

## Dataset Source

The Credit Card Fraud Detection dataset was obtained from Kaggle. Due to GitHub file size limits, the raw dataset is not included in this repository.
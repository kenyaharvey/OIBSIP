# Wine Quality Prediction

## Project Overview

This project uses machine learning classification models to predict whether a wine is classified as good or bad based on its physicochemical properties.

The project demonstrates an end-to-end machine learning workflow, including data validation, exploratory data analysis, feature engineering, model training, evaluation, and model comparison.

## Objective

Train and compare multiple classification models to predict wine quality using chemical properties such as acidity, density, sulphates, sulfur dioxide, and alcohol content.

The models evaluated are:

- Random Forest
- Stochastic Gradient Descent (SGD)
- Support Vector Classifier (SVC)

## Dataset

The Wine Quality dataset contains physicochemical measurements of red wine samples and their corresponding quality scores.

The original quality scores range from 3 to 8. For this classification project, the quality scores were converted into two categories:

- `0` = Bad quality
- `1` = Good quality

The dataset contains 1,143 observations and 11 predictor features used for modeling.

## Data Quality

Before modeling, the dataset was examined for common data-quality issues.

The analysis checked for:

- Missing values
- Duplicate records
- `ERROR` values
- `UNKNOWN` values
- Data types
- Dataset dimensions

No missing values or `ERROR`/`UNKNOWN` values were found. One duplicate record was identified during the data-quality assessment.

## Exploratory Data Analysis

Exploratory analysis included:

- Distribution plots for the chemical features
- Wine quality class distribution
- Correlation analysis
- Correlation heatmap

Alcohol had the strongest positive linear correlation with wine quality, while volatile acidity had the strongest negative linear correlation.

## Feature Engineering

The original wine quality score was converted into a binary classification target.

The resulting target distribution was:

- Bad quality: 522 wines
- Good quality: 621 wines

The binary classification approach was selected to simplify the prediction task and provide a clearer distinction between lower- and higher-quality wines.

## Model Preparation

The dataset was divided into training and testing sets using an 80/20 stratified split.

- Training set: 914 observations
- Testing set: 229 observations

Stratification was used to preserve the proportion of good- and bad-quality wines in both datasets.

Feature scaling was performed using `StandardScaler` for the SGD and SVC models.

## Machine Learning Models

### Random Forest

Random Forest was selected because it can capture nonlinear relationships and interactions between physicochemical features. It also provides feature importance measurements.

### Stochastic Gradient Descent

SGD was included as a computationally efficient linear classification model. Standardized features were used because SGD is sensitive to feature scale.

### Support Vector Classifier

SVC was included as another classification approach capable of identifying decision boundaries between the two wine-quality classes. Standardized features were used for this model.

## Model Results

| Model | Accuracy | Bad F1 | Good F1 |
|---|---:|---:|---:|
| Random Forest | 80.8% | 78% | 83% |
| SVC | 78.6% | 76% | 80% |
| SGD | 62.9% | 48% | 71% |

Random Forest achieved the highest overall accuracy and strongest F1-score performance across the two classes.

## Random Forest Feature Importance

The Random Forest model identified the following features as the most influential:

1. Alcohol — 19.8%
2. Sulphates — 13.4%
3. Total sulfur dioxide — 10.3%
4. Volatile acidity — 10.0%
5. Density — 8.4%

Alcohol was the most influential predictor in the Random Forest model.

Feature importance indicates predictive contribution within the model and should not be interpreted as evidence of causation.

## Conclusion

Random Forest was the strongest-performing model among the three classifiers tested.

It achieved 80.8% test accuracy and provided relatively balanced performance across the bad- and good-quality wine classes. SVC performed slightly lower at 78.6%, while SGD achieved 62.9%.

Based on the results from this project, Random Forest is the most suitable model for further development.

However, additional validation, hyperparameter tuning, cross-validation, and testing on new wine samples would be recommended before considering real-world deployment.

## Technologies

- Python
- pandas
- NumPy
- scikit-learn
- Matplotlib
- Seaborn
- Jupyter Notebook

## Project Structure

```text
wine-quality-prediction/
├── README.md
├── .gitignore
├── data/
│   └── winequality-red.csv
├── images/
│   ├── histograms.png
│   ├── correlation.png
│   ├── correlation_heatmap.png
│   ├── random_forest_confusion_matrix.png
│   ├── random_forest_feature_importance.png
│   ├── sgd_confusion_matrix.png
│   └── svc_confusion_matrix.png
└── notebooks/
    └── wine_quality_prediction.ipynb
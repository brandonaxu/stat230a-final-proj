# Predicting Obesity from Behavioral Data
## Project Overview
This project explores the use of behavioral and demographic features to predict obesity using machine learning techniques. Leveraging a synthetic dataset from the UCI Machine Learning Repository, the team investigates how factors such as eating habits, physical activity, and family history influence obesity status.

Notably, our model outperformed a recent approach by Sun et al. (2024) published in Frontiers in Big Data, which proposed BMI-obfuscated behavioral models for obesity prediction. While their best-performing model achieved around 80.7% accuracy, our binary classification model using elastic-net regularized logistic regression achieved a significantly higher 85.6% accuracy—an almost 5% improvement in predictive performance.

## How to Run: 
First run the `data_preprocessing.ipynb` notebook to retrieve all of the datasets needed for this project. Then, run `data_analysis.ipynb` and `data_visualization.ipynb` to look at training process and visualization results

## Objective
To build accurate classification models that predict whether an individual is obese (binary classification), and optionally which specific weight category they belong to (multiclass classification), using non-BMI behavioral and demographic data.

## Dataset
**Source**: UCI ML Repository (2022)

**Rows**: 2,111 individuals

**Features**: Demographics, lifestyle habits, eating behavior, alcohol use, physical activity, etc.

**Target (Binary)**: Obese vs. Non-Obese

**Target (Multiclass)**: 7 obesity-related classes including Normal, Overweight, Obesity Types I–III, etc.

## Preprocessing & Feature Engineering
**Exclusion of BMI**: To avoid trivial prediction, height was excluded and weight retained.

**Transformations**: Logarithmic (log1p), exponential (exp), and polynomial up to degree 2

**Encoding**: One-hot for categorical variables

**Scaling**: Standardization of numeric features

**Feature Selection**: LASSO regularization (λ = 0.1, 1, 10) to reduce dimensionality

**Final Features**: 64 engineered features

## Models
Binary Classification
**Model**: Logistic Regression with Elastic-Net regularization

**Best Config**: C=1, l1_ratio=0.75, solver=saga

**Performance**:

**Accuracy**: 96.2%

**Precision/Recall/F1**: 95.98%

**AUC**: 0.99

Multiclass Classification
**Model**: Multinomial Logistic Regression with L1 penalty

**Best Config**: C=10

**Performance**:

**Accuracy**: 85.6%

High F1 Scores for edge classes like Obesity Type II, III, and Insufficient Weight (all > 0.90)

Lower accuracy in distinguishing intermediate classes like Overweight Level I

## Key Findings
**Strong Predictors**:

Weight-based interaction terms (e.g., FCVC * Weight, NCP * Weight)

Lifestyle factors such as alcohol intake (CALC), eating out (CAEC), and screen time (TUE)

Behavioral patterns involving food consumption and physical activity

**Counterintuitive Observations**:

Being male and increased screen time had negative correlations with obesity in the binary model

## Limitations
**Cross-sectional Data**: Limits predictive use over time or causal interpretation

**Self-reported Features**: Introduces potential recall and social desirability biases

**Limited External Validity**: Dataset comprises individuals from Latin America (Mexico, Peru, Colombia)

## Conclusion
This project demonstrates that obesity can be effectively predicted using non-BMI features through careful engineering and regularization. The binary model performs exceptionally well, and the multiclass model provides granular insights, particularly at the extremes of the obesity spectrum. While promising, further validation with longitudinal and diverse data is necessary for practical deployment.

## References
UCI Obesity Dataset

Sun et al. (2024), BMI obfuscation improves generalizability in obesity prediction using behavioral data, Frontiers in Big Data


---
layout: default
title: Model
---

# Model

## Framing the Problem

This project is framed as a **binary classification problem**, where the goal is to predict whether a power outage will last longer than 48 hours.

- Target variable: `severe_48h`  
- Type: Classification  

A key constraint is that only features available at the **start of the outage** are used. This avoids data leakage and ensures the model reflects a realistic prediction scenario.

---

## Features Used

The model uses a combination of numerical and categorical features:

**Numerical features:**
- start year  
- population  
- anomaly level  

**Categorical features:**
- cause category  
- cause category detail  
- climate category  
- NERC region  
- state  
- month, hour, and day of week  

These features capture both environmental and infrastructure-related factors that may influence outage severity.

---

## Baseline Model

The baseline model is a **logistic regression model**.

### Preprocessing

- Missing numerical values were filled using the median  
- Missing categorical values were filled using the most frequent value  
- Categorical variables were one-hot encoded  
- Numerical features were standardized  

### Performance

- Accuracy ≈ 0.81  
- AUC ≈ 0.83  

Because severe outages are less common, recall is especially important. A balanced version of the model improved recall for severe outages, helping reduce false negatives.

---

## Model Improvements

Several improvements were explored to enhance performance:

### 1. Feature Engineering

- Applied a log transformation to population to reduce skew  
- Created an interaction feature combining outage cause and climate  

These changes aimed to provide the model with more meaningful patterns.

---

### 2. Hyperparameter Tuning

Cross-validation was used to tune logistic regression parameters:

- Regularization strength (C)  
- Penalty type (L1 vs L2)  

The best model used L2 regularization with default strength.

---

## Final Model Performance

- Final AUC ≈ 0.83  

The improvements resulted in only a slight increase in performance, suggesting that the baseline model already captured most of the useful signal in the data.

---

## Fairness Analysis

To evaluate fairness, model performance was compared across regions using recall.

- West recall: 0.58  
- East recall: 0.79  
- Difference: -0.21  
- p-value = 0.026  

Since the p-value is below 0.05, we reject the null hypothesis of equal performance.

This indicates that the model performs significantly worse at identifying severe outages in Western regions, suggesting potential regional bias.

---

## Key Takeaways

- Logistic regression performs well for this problem, achieving strong AUC  
- Feature engineering provided only marginal improvements  
- Recall is more important than accuracy due to class imbalance  
- The model shows evidence of regional bias, which would need to be addressed before real-world use  

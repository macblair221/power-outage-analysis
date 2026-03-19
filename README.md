# Power Outage Severity Analysis  
McAllister Blair  

---
<div class="section">
## Introduction

This project analyzes major U.S. power outages to understand what makes some outages last significantly longer than others. Specifically, I investigate whether we can predict if an outage will last more than 48 hours using only information available at the start of the event.

This question matters because prolonged outages can have serious economic and safety consequences. If utilities can identify high-risk outages early, they can prioritize response efforts more effectively.

This dataset contains approximately 1,535 observations. Key variables used in this analysis include:

- `duration_minutes`: total outage duration  
- `customers_affected`: number of customers impacted  
- `cause_category`: general cause of the outage  
- `climate_category`: warm, cold, or normal climate condition  
- `severe_48h`: whether the outage lasted longer than 48 hours  

The central question of this project is:

**What factors available at the start of an outage influence whether it becomes severe (lasting more than 48 hours)?**
</div>
---

## Data Cleaning and Exploratory Data Analysis

### Data Cleaning

The dataset required several preprocessing steps before analysis:

- Removed the first row containing unit descriptions instead of observations  
- Standardized column names for consistency  
- Combined date and time columns into datetime features  
- Created `duration_minutes` from outage start and restoration times  
- Created `severe_48h`, a binary indicator for outages lasting longer than 48 hours  
- Converted numeric-like columns to proper numeric types  
- Removed redundant features (e.g., postal code vs state)  
- Handled missing values appropriately  

These steps ensured the dataset was clean and suitable for analysis.

---

### Exploratory Data Analysis

The distribution of outage durations is highly right-skewed, meaning most outages are relatively short, while a small number last significantly longer.

<iframe src="assets/outages_dist.html" width="100%" height="400" frameborder="0"></iframe>

There is a positive relationship between the number of customers affected and outage duration. Larger outages tend to last longer, though there is still substantial variability.

<iframe src="assets/customers_vs_duration.html" width="100%" height="400" frameborder="0"></iframe>

The proportion of severe outages is very similar across climate categories, suggesting that climate alone may not strongly determine outage severity.

<iframe src="assets/severe_by_climate.html" width="100%" height="400" frameborder="0"></iframe>

---

### Interesting Aggregates

| cause_category                | avg_duration | severe_rate | count |
|:------------------------------|-------------:|------------:|------:|
| fuel supply emergency         | 13493.5      | 0.4118      | 38    |
| severe weather                | 3883.18      | 0.4115      | 744   |
| public appeal                 | 1468.45      | 0.1449      | 69    |
| system operability disruption | 728.87       | 0.0551      | 123   |
| intentional attack            | 429.98       | 0.0215      | 403   |
| equipment failure             | 1818         | 0.0167      | 55    |
| islanding                     | 200.55       | 0.0000      | 44    |

Outage severity varies significantly across cause categories. Severe weather stands out as especially important because it combines a high rate of severe outages with a large number of events, making it one of the primary drivers of prolonged outages.

---

## Assessment of Missingness

One key variable, `customers_affected`, contains missing values. This missingness is unlikely to be completely random, since utilities may have difficulty estimating the number of affected customers during large or complex outages.

A permutation test shows that missingness depends on `cause_category`, but not on `climate_category`. This suggests the missingness mechanism is likely **Missing At Random (MAR)** rather than completely random.

<iframe src="assets/missingness_cause.html" width="100%" height="400" frameborder="0"></iframe>

---

## Hypothesis Testing

**Null Hypothesis:**  
The proportion of prolonged outages (lasting more than 48 hours) is the same during warm and cold climate conditions.

**Alternative Hypothesis:**  
The proportion of prolonged outages differs between warm and cold climate conditions.

A permutation test was conducted using the difference in proportions as the test statistic.

- Observed difference ≈ 0.005  
- p-value = 0.925  

Since the p-value is very large, we fail to reject the null hypothesis. This suggests there is no significant evidence that climate category alone affects whether an outage becomes prolonged.

<iframe src="assets/permutation_test.html" width="100%" height="400" frameborder="0"></iframe>

---

## Framing a Prediction Problem

This project is framed as a **binary classification problem**, where the goal is to predict whether an outage will last longer than 48 hours.

- Target variable: `severe_48h`  
- Type: Classification  

Only features available at the start of the outage are used to avoid data leakage, ensuring the model reflects a realistic prediction scenario.

---

## Baseline Model

A logistic regression model was used as the baseline.

Preprocessing steps included:

- Median imputation for numerical features  
- Most frequent imputation for categorical features  
- One-hot encoding of categorical variables  
- Standardization of numerical variables  

The baseline model achieved:

- AUC ≈ 0.83  
- Accuracy ≈ 0.81  

Because severe outages are less common, recall is particularly important. A balanced version of the model improved recall for severe outages, reducing the risk of missing critical events.

---

## Final Model

The final model builds on the baseline through simple feature engineering:

- Log transformation of population  
- Interaction feature combining outage cause and climate  

Hyperparameters were tuned using cross-validation.

Despite these improvements, performance increased only slightly:

- Final AUC ≈ 0.83  

This suggests that the baseline model already captures most of the predictive signal in the data, and that more complex modeling may be required for further improvements.

---

## Fairness Analysis

To evaluate fairness, model performance was compared between Western and Eastern regions using recall.

- West recall: 0.58  
- East recall: 0.79  
- Difference: -0.21  
- p-value = 0.026  

Since the p-value is below 0.05, we reject the null hypothesis of equal performance. This indicates that the model performs significantly worse at identifying severe outages in Western regions.

This suggests potential regional bias in the model, which would be important to address before using it in real-world decision-making.

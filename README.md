# Power Outage Severity Analysis
McAllister Blair

---

## Introduction
Power outages are critical infrastructure failures that can have significant economic and social impacts. Understanding what factors contribute to longer and more severe outages is important for improving resilience and response strategies.

This project uses the Major Power Outages dataset, which contains records of large outages across the United States. Each row represents a major outage event, defined as affecting at least 50,000 customers or causing at least 300 MW of demand loss.

This dataset contains approximately 1,535 rows. The key variables used in this analysis include:

- `duration_minutes`: total outage duration  
- `customers_affected`: number of customers impacted  
- `cause_category`: general cause of the outage  
- `climate_category`: warm, cold, or normal climate condition  
- `severe_48h`: whether the outage lasted longer than 48 hours  

The central question of this project is:

**What factors (given at the start of an outage) influence whether a power outage becomes severe (lasting more than 48 hours)?**

This question matters because identifying these factors can help utilities better predict and prepare for high-impact outages.

## Data Cleaning and Exploratory Data Analysis
### Data Cleaning

The dataset required several preprocessing steps before analysis:

- Removed the first row containing unit descriptions instead of observations  
- Standardized column names for consistency  
- Combined date and time columns into usable datetime formats  
- Created `duration_minutes` from outage start and restoration times  
- Created `severe_48h`, a binary indicator for outages lasting longer than 48 hours  
- Converted numeric-like columns to proper numeric types  
- Handled missing values appropriately  

These steps ensured the dataset was clean and suitable for analysis.

### Exploratory Data Analysis

The distribution of outage durations is highly right-skewed, with most outages lasting a relatively short time and a smaller number lasting much longer.

<iframe src="assets/outages_dist.html" width="100%" height="400" style="border:none;"></iframe>

There is a positive relationship between the number of customers affected and outage duration, though the relationship is not perfectly linear.

<iframe src="assets/customers_vs_duration.html" width="100%" height="400" style="border:none;"></iframe>

The proportion of severe outages is similar across climate categories, suggesting climate alone may not strongly determine outage severity.

<iframe src="assets/severe_by_climate.html" width="100%" height="400" style="border:none;"></iframe>

### Interesting Aggregates

| cause_category                |   avg_duration |   severe_rate |   count |
|:------------------------------|---------------:|--------------:|--------:|
| fuel supply emergency         |      13493.5   |     0.411765  |      38 |
| severe weather                |       3883.18  |     0.411533  |     744 |
| public appeal                 |       1468.45  |     0.144928  |      69 |
| system operability disruption |        728.87  |     0.0551181 |     123 |
| intentional attack            |        429.98  |     0.0215311 |     403 |
| equipment failure             |       1818     |     0.0166667 |      55 |
| islanding                     |        200.545 |     0         |      44 |

Outage severity varies across cause categories, with severe weather and fuel supply emergencies having the highest rates of prolonged outages.
## Assessment of Missingness

## Hypothesis Testing

## Framing a Prediction Problem

## Baseline Model

## Final Model

## Fairness Analysis


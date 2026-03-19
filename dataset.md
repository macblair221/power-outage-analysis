---
layout: default
title: Dataset
nav_order: 2
---

<div class="section">

## Source
This project uses the **Major Power Outages in the United States** dataset from Purdue University's Laboratory for Advancing Sustainable Critical Infrastructure (LASCI).
It contains historical records of large power outages across U.S. states along with information about outage causes, electricity demand, and demographic characteristics.

Dataset source:  
[Power Outage Dataset](https://engineering.purdue.edu/LASCI/research-data/outages)

Data dictionary:  
[Data Dictionary](https://www.sciencedirect.com/science/article/pii/S2352340918307182)
</div>

<div class="section">

## Overview

A major outage in this dataset refers to an event that affected at least 50,000 customers or caused at least 300 MW of unplanned firm load loss.

The data combines outage event information with state-level climate, electricity consumption, economic, and land-use characteristics. 

</div>

<div class="section">
  
## What the Dataset Includes

The dataset includes information about:

- when the outage happened
- where the outage occurred
- how long the outage lasted
- how many customers were affected
- the reported cause of the outage
- electricity demand loss
- state-level electricity pricing and consumption
- regional economic and demographic characteristics

</div>

<div class="section">
  
## Important Variables

| Variable | Description |
|--------|-------------|
| YEAR | Year the outage occurred |
| MONTH | Month the outage occurred |
| U.S._STATE | State where the outage occurred |
| NERC.REGION | NERC region involved in the outage |
| OUTAGE.START.DATE | Date the outage began |
| OUTAGE.START.TIME | Time the outage began |
| OUTAGE.RESTORATION.DATE | Date power was restored |
| OUTAGE.RESTORATION.TIME | Time power was restored |
| OUTAGE.DURATION | Duration of outage in minutes |
| CUSTOMERS.AFFECTED | Number of customers impacted |
| DEMAND.LOSS.MW | Peak demand loss during the outage |
| CAUSE.CATEGORY | Broad outage cause category |
| CAUSE.CATEGORY.DETAIL | More detailed outage cause description |
| CLIMATE.REGION | U.S. climate region |
| CLIMATE.CATEGORY | Warm, Cold, or Normal climate episode |

</div>

<div class="section">
  
## Data Cleaning

I cleaned the dataset by:

- removing the first row, which stores units instead of outage observations
- renaming column headers to a consistent workable format
- dropping or handling missing values where necessary
- converting date and time columns into usable formats
- selecting the most relevant variables for analysis and modeling
  
</div>

<div class="section">
  
## Limitations

Some variables contain missing values, and some outage causes are more detailed than others. Because the data is aggregated from several public sources, reporting consistency may vary across states and years.

</div>

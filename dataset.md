---
layout: default
title: Dataset
---

# Dataset

## Source

This project uses the Major Power Outages in the United States dataset from Purdue University's Laboratory for Advancing Sustainable Critical Infrastructure (LASCI). It contains historical records of large power outages across U.S. states along with information about outage causes, electricity demand, and demographic characteristics.

Dataset source:  
[Power Outage Dataset](https://engineering.purdue.edu/LASCI/research-data/outages)

Data dictionary:  
[Data Dictionary](https://www.sciencedirect.com/science/article/pii/S2352340918307182)

## Overview

A major outage in this dataset refers to an event that affected at least 50,000 customers or caused at least 300 MW of unplanned firm load loss.

The data combines outage event information with state-level climate, electricity consumption, economic, and land use characteristics.

## What the Dataset Includes

The dataset includes information about:

- when the outage happened
- where the outage occurred
- how long the outage lasted
- how many customers were affected
- the reported cause of the outage
- electricity demand loss
- state level electricity pricing and consumption
- regional economic and demographic characteristics

## Important Variables

| Variable | Description |
|----------|-------------|
| YEAR | Year the outage occurred |
| MONTH | Month the outage occurred |
| U.S._STATE | State where the outage occurred |
| NERC.REGION | NERC region involved |
| OUTAGE.START.DATE | Start date |
| OUTAGE.START.TIME | Start time |
| OUTAGE.RESTORATION.DATE | End date |
| OUTAGE.RESTORATION.TIME | End time |
| OUTAGE.DURATION | Duration in minutes |
| CUSTOMERS.AFFECTED | Customers impacted |
| DEMAND.LOSS.MW | Demand loss |
| CAUSE.CATEGORY | Outage cause |
| CLIMATE.CATEGORY | Climate type |

## Data Cleaning

I cleaned the dataset by:

- removing the first row containing units instead of outage observations
- standardizing column names
- converting date and time fields into usable datetime formats
- handling missing values where necessary
- selecting relevant variables for analysis and modeling

## Limitations

Some variables contain missing values, and some outage causes are more detailed than others. Because the data is aggregated from several public sources, reporting consistency may vary across states and years.

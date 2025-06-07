# The Correlation Between Electricity Usage and Power Outages

## Introduction

This project analyzes a dataset containing detailed information on major power outages across the United States. The goal is to explore the correlation between the **number of power outages** and **electricity usage** in different regions over time.

Understanding this relationship is critical because power outages have significant economic and social impacts. By studying outage patterns alongside electricity consumption, stakeholders can better prepare for and mitigate the effects of severe weather on the power grid.

The dataset used in this project is available as a single Excel file with 55 variables, accessible [here](https://engineering.purdue.edu/LASCI/research-data/outages/outagerisks). All measurements are in the Imperial System. This dataset provides valuable insights into weather-induced power outages and regional characteristics influencing outage risks.

## Dataset Overview

- **Number of rows:** *1534*  
- **Relevant columns:**

| Column Name          | Description                                                  |
|----------------------|--------------------------------------------------------------|
| `YEAR`               | Year when the outage occurred                                |
| `MONTH`              | Month of the outage                                          |
| `U.S._STATE`         | U.S. state where the outage happened                         |
| `OUTAGE.START`       | Date/time when the outage began                              |
| `OUTAGE.RESTORATION` | Date/time when power was restored                            |
| `CAUSE.CATEGORY`     | General cause of the outage                                  |
| `CAUSE.CATEGORY.DETAIL` | More detailed description of outage cause                 |
| `HURRICANE.NAMES`    | Name of associated hurricane, if any                         |
| `OUTAGE.DURATION`    | Duration of the outage (minutes)                             |
| `CUSTOMERS.AFFECTED` | Number of customers affected by the outage                   |
| `RES.SALES`          | Residential electricity sales (kWh) that month               |
| `COM.SALES`          | Commercial electricity sales (kWh) that month                |
| `IND.SALES`          | Industrial electricity sales (kWh) that month                |
| `TOTAL.SALES`        | Total electricity sales (kWh) that month                     |
| `RES.PERCEN`         | Percentage of residential electricity sales                  |
| `COM.PERCEN`         | Percentage of commercial electricity sales                   |
| `IND.PERCEN`         | Percentage of industrial electricity sales                   |

The analysis focuses on these columns to examine how electricity usage in different sectors correlates with the frequency and duration of power outages.



## Data Cleaning and Exploratory Data Analysis

## Assessment of Missingness

## Hypothesis Testing

## Framing a Prediction Problem

## Baseline Model

## Final Model

## Fairness Analysis

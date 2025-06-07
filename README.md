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

The raw dataset required several cleaning and preprocessing steps to ensure accurate and meaningful analysis, particularly because outage start and restoration times were originally stored as separate date and time columns. These steps align closely with the data generating process, where outage events have specific start and end timestamps.

### Cleaning Steps

1. **Combining Date and Time Columns**  
   The dataset contained separate columns for the date and time of outage start (`OUTAGE.START.DATE` and `OUTAGE.START.TIME`) and outage restoration (`OUTAGE.RESTORATION.DATE` and `OUTAGE.RESTORATION.TIME`). To properly analyze outage durations and timelines, these were combined into single datetime columns: `OUTAGE.START` and `OUTAGE.RESTORATION`.  

2. **Selecting Relevant Columns**  
   Only columns essential to the research question were kept. This helps keep the dataset manageable and focused on variables tied to power outages and electricity usage, such as outage times, causes, affected customers, and electricity sales data.

3. **Adding the Column SALE_PER_YEAR**  
   A new column SALE_PER_YEAR was added to the dataset since the sale data was originally for a specific month. Since my analysis would be focusing on number of outages for each state per year, I decided to add this column for simplicity moving forward.

|   YEAR |   MONTH | U.S._STATE   | OUTAGE.START        | OUTAGE.RESTORATION   | CAUSE.CATEGORY     | CAUSE.CATEGORY.DETAIL   |   HURRICANE.NAMES |   OUTAGE.DURATION |   CUSTOMERS.AFFECTED |   RES.SALES |   COM.SALES |   IND.SALES |   TOTAL.SALES |   RES.PERCEN |   COM.PERCEN |   IND.PERCEN |   SALE_PER_YEAR |
|-------:|--------:|:-------------|:--------------------|:---------------------|:-------------------|:------------------------|------------------:|------------------:|---------------------:|------------:|------------:|------------:|--------------:|-------------:|-------------:|-------------:|----------------:|
|   2011 |       7 | Minnesota    | 2011-07-01 17:00:00 | 2011-07-03 20:00:00  | severe weather     | nan                     |               nan |              3060 |                70000 |     2332915 |     2114774 |     2113291 |       6562520 |      35.5491 |      32.225  |      32.2024 |        11825188 |
|   2014 |       5 | Minnesota    | 2014-05-11 18:38:00 | 2014-05-11 18:39:00  | intentional attack | vandalism               |               nan |                 1 |                  nan |     1586986 |     1807756 |     1887927 |       5284231 |      30.0325 |      34.2104 |      35.7276 |        10858304 |
|   2010 |      10 | Minnesota    | 2010-10-26 20:00:00 | 2010-10-28 22:00:00  | severe weather     | heavy wind              |               nan |              3000 |                70000 |     1467293 |     1801683 |     1951295 |       5222116 |      28.0977 |      34.501  |      37.366  |        16971201 |
|   2012 |       6 | Minnesota    | 2012-06-19 04:30:00 | 2012-06-20 23:00:00  | severe weather     | thunderstorm            |               nan |              2550 |                68200 |     1851519 |     1941174 |     1993026 |       5787064 |      31.9941 |      33.5433 |      34.4393 |         5787064 |
|   2015 |       7 | Minnesota    | 2015-07-18 02:00:00 | 2015-07-19 07:00:00  | severe weather     | nan                     |               nan |              1740 |               250000 |     2028875 |     2161612 |     1777937 |       5970339 |      33.9826 |      36.2059 |      29.7795 |        11569825 |

## Assessment of Missingness

## Hypothesis Testing

## Framing a Prediction Problem

## Baseline Model

## Final Model

## Fairness Analysis

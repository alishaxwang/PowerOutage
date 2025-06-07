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

### EDA
This plot shows the distribution of all recorded power outages in the dataset, with durations converted from minutes to hours. Most outages cluster toward the lower end of the spectrum, though a few long-lasting events stretch the upper range.

<iframe
  src="assets/Distribution_of_Outage_Duration.html"
  width="1000"
  height="600"
  frameborder="0"
></iframe>

To get a clearer view of the more common outage durations, this version filters out extreme values above 250 hours. The resulting histogram reveals a right-skewed distribution, with the majority of outages lasting under 50 hours.

<iframe
  src="assets/Distribution_of_Short_Outages.html"
  width="1000"
  height="600"
  frameborder="0"
></iframe>

This interactive choropleth map shows the number of power outages by U.S. state, with darker colors representing more outages. It helps visualize geographic patterns and identify states most affected by power disruptions.
<iframe
  src="assets/outage_map.html"
  width="1000"
  height="600"
  frameborder="0"
></iframe>

This pivot table summarizes power outage data by state and year. For each state-year pair, it shows the total number of outages (NUM_OUTAGES) recorded and the total electricity usage (TOTAL_USAGE) for that year, enabling analysis of how outage frequency relates to annual electricity consumption across different states and years.

| U.S._STATE   |   YEAR |   NUM_OUTAGES |   TOTAL_USAGE |
|:-------------|-------:|--------------:|--------------:|
| Alabama      |   2000 |             2 |      15295312 |
| Alabama      |   2013 |             1 |       6479167 |
| Alabama      |   2014 |             1 |       7907462 |
| Alabama      |   2015 |             1 |       8934377 |
| Alaska       |   2000 |             0 |             0 |


## Assessment of Missingness
I believe that the OUTAGE.START column could be considered NMAR (Not Missing At Random), which means that the missingness depends on the actual outage start time itself. For example, outages that begin during chaotic or emergency situations might have missing or poorly recorded start times because data collection is disrupted precisely when outages start. In that case, whether the start time is missing depends on the very event timing, which is unobserved—making the missingness NMAR.

The permutation test uses the variance of the group means of the target variable as its test statistic. Specifically, for each grouping column (e.g., CAUSE.CATEGORY or U.S._STATE), the dataset is divided into groups, and the mean value of the binary missingness indicator (missing_hurricane) is calculated for each group. The test statistic is the variance across these group means.

The permutation tests show that the missingness of HURRICANE.NAMES is significantly related to CAUSE.CATEGORY (p = 0.048), indicating that whether a hurricane name is missing depends on the cause of the outage. In contrast, missingness does not appear to depend on the state (U.S._STATE, p = 0.195). This suggests that missing hurricane names are not random but are influenced by the outage cause, supporting the idea that the missingness is Missing At Random (MAR) with respect to cause category.

This figure displays the counts of different outage causes (CAUSE.CATEGORY) separated by whether the hurricane name data (HURRICANE.NAMES) is missing or not. Each cause category has two bars: one representing the number of outages with missing hurricane data, and the other for outages with recorded hurricane information. This visualization helps illustrate that the missingness of HURRICANE.NAMES is dependent on CAUSR.CATEGORY.

<iframe
  src="assets/cause_category_missingness.html"
  width="1000"
  height="600"
  frameborder="0"
></iframe>

## Hypothesis Testing
To assess whether there is a statistically significant relationship between the number of power outages and total electricity usage, we conducted a permutation test using Pearson correlation as the test statistic.
The null hypothesis (H₀) states that there is no association between the number of outages and electricity usage, any observed correlation is due to random chance. 
The alternative hypothesis (H₁) is that there is an association between these variables.

The observed Pearson correlation between the number of outages and electricity usage was 0.7266, indicating a strong positive correlation: as electricity usage increases, the number of power outages also tends to increase. To evaluate its significance, we randomly permuted the electricity usage values 10,000 times and recalculated the correlation each time. The resulting p-value was 0.0000, meaning that in none of the permutations did a correlation as extreme as the observed one occur by chance.

Using a standard significance level of α = 0.05, we find strong evidence against the null hypothesis. This suggests that the observed correlation is unlikely to be due to random variation alone, and we have statistical support for a meaningful association between the number of power outages and electricity usage. 

The permutation approach is appropriate here because it does not assume normality and directly tests the null hypothesis using the empirical data. It also doesn’t assume a known population distribution and works well when the full population data isn’t available. Instead, it estimates significance by shuffling the observed data to create a null distribution.
I chose pearson correlation as my test statistic because it measures the strength and direction of the linear relationship between two continuous variables, which fits the question about outages and usage.
I chose alpha level of 0.05 since that's the common standard that balances detecting true effects while limiting false positives.


<iframe
  src="assets/permutation_test_histogram.html"
  width="1000"
  height="600"
  frameborder="0"
></iframe>

## Framing a Prediction Problem
In this project, I aim to predict the number of power outages in each U.S. state per year based on its electricity usage. This is a regression problem, as the response variable, NUM_OUTAGES, is a continuous numerical value rather than a discrete category.

The response variable is NUM_OUTAGES, which counts the number of reported power outages in a given state and year. I selected this variable because understanding and forecasting outage frequency based on electricity demand is crucial for infrastructure planning and energy resilience.

To build the predictive model, I used a Random Forest Regressor, a robust and flexible ensemble learning method that performs well with nonlinear relationships and does not require heavy preprocessing.

To evaluate model performance, I used the R² score, which measures how well the model explains the variability in the number of outages. A higher R² value indicates better predictive accuracy.

## Baseline Model
My baseline model is a Random Forest Regressor used to predict the number of power outages (NUM_OUTAGES) based on two features: TOTAL_USAGE and U.S._STATE. The feature TOTAL_USAGE is quantitative, while U.S._STATE is a nominal categorical variable. There are no ordinal variables in this model.

To prepare the features for modeling, I applied standard scaling to the numeric feature and one-hot encoding to the categorical feature using a ColumnTransformer within a scikit-learn pipeline. This preprocessing ensures that the numeric values are on a similar scale and that categorical data is converted into a format suitable for machine learning models.

My model achieved an R² score of 0.6760 on the test set, which indicates that approximately 67.6% of the variance in outage counts can be explained by the features in the model. I believe this indicates good performance, suggesting the model captures meaningful relationships, though there may still be room for improvement with additional features or more complex tuning.

## Final Model
To improve prediction performance, I added the following features:

OUTAGE.DURATION (average per year per state): Longer outages may indicate more severe disruptions, which can correlate with higher outage counts.

CUSTOMERS.AFFECTED (total per year per state): Outages affecting more people likely reflect larger or more frequent incidents.

HURRICANE.NAMES (count of named storms per year per state): Hurricanes are a known cause of outages, so this count gives a measure of storm-related disruptions.

These features are meaningful because they capture severity, scale, and environmental factors that influence power outages. Including them provides the model with richer context beyond electricity usage alone.

I used GridSearchCV to tune hyperparameters with a 5-fold cross-validation strategy. The best-performing hyperparameters were:

n_estimators = 200

max_depth = None (allowing trees to fully expand)

min_samples_split = 2 (default, allowing detailed splits)

The final model achieved an R² score of 0.7425, a clear improvement over the baseline model’s R² of 0.6760. This increase suggests that the added features allowed the model to better capture the variability in the number of outages across states and years.

## Fairness Analysis
Group X and Group Y:
Group X consists of test samples from Western states, and Group Y consists of test samples from Eastern states.

Evaluation Metric:
Root Mean Squared Error (RMSE) was used to measure prediction error separately for each group.

Null Hypothesis (H₀):
There is no difference in model prediction error between the West and East regions; i.e., the RMSE difference (West - East) is zero.

Alternative Hypothesis (H₁):
The RMSE in the West region is greater than the RMSE in the East region, indicating worse model performance in the West.

Test Statistic:
The observed difference in RMSE between West and East (RMSE_West − RMSE_East), which was 0.4400.

Significance Level:
α = 0.05 (5%)

Resulting p-value:
0.2463

Conclusion:
Since the p-value (0.2463) is greater than the significance level (0.05), we fail to reject the null hypothesis. There is insufficient evidence to conclude that the model performs significantly worse in the Western states compared to the Eastern states. The observed difference in RMSE could plausibly be due to chance. Therefore my model was fair.
# India CPI Inflation Analysis (2013–2023)

An Excel-based data analytics project exploring India's Consumer Price Index (CPI), inflation trends, food-price movements, COVID-period inflation patterns, and the relationship between crude-oil price changes and CPI categories.

## Project Overview

This project uses monthly CPI data from 2013 to May 2023 to demonstrate a practical data-analysis workflow in Microsoft Excel and Power Query. The workbook covers data preparation, missing-value treatment, percentage-change calculations, trend analysis, PivotTable summaries, visualisation, and correlation analysis.

The project is designed to show how raw time-series data can be cleaned, organised, analysed, and translated into findings that are easier to interpret.

## Objectives

* Compare selected CPI category values across Rural, Urban, and Rural+Urban sectors.
* Calculate annual inflation using annual-average General Index values.
* Examine month-on-month (MoM) changes in Food and Beverages CPI.
* Compare year-on-year (YoY) inflation across selected categories around the onset of COVID-19.
* Explore the correlation between monthly imported crude-oil price changes and monthly CPI category changes.
* Document how missing CPI observations were estimated and incorporated into the prepared dataset.

## Tools and Techniques

* **Microsoft Excel** — formulas, tables, charts, and formatting
* **Power Query** — data cleaning, filtering, combining data, and refreshable preparation steps
* **PivotTables** — summarising inflation rates across categories and periods
* **Time-series analysis** — annual, month-on-month, and year-on-year comparisons
* **Linear interpolation** — estimating selected missing monthly CPI observations
* **Correlation analysis** — examining linear relationships between monthly crude-oil and CPI changes

## Workbook Guide

|Worksheet|Purpose|
|-|-|
|`Raw CPI`|Original CPI source data, retained as a reference.|
|`Cleaned CPI data`|Prepared CPI dataset with date and month-number fields for analysis.|
|`analysis 1`|Compares selected CPI category values across Rural, Urban, and Rural+Urban for May 2023 and calculates each category's share of the selected category values.|
|`Analysis 2`|Calculates annual-average General Index values and year-on-year inflation for 2017–2022, using 2016 as the comparison year.|
|`Analysis 3`|Examines monthly Food and Beverages CPI changes from June 2022 to May 2023 and compares food-category index values across the same period.|
|`Analysis 4`|Compares average YoY inflation for selected CPI categories across pre-COVID, COVID-onset, and post-onset periods.|
|`Analysis 5`|Compares monthly crude-oil price changes with CPI category changes and summarises correlation coefficients.|
|`Rural+Urban Combined`|Prepared Rural+Urban time series used by the analyses.|
|`Null imputation`|Support sheet documenting estimated CPI values for missing observations in April and May 2020.|
|`April19`|Support sheet containing estimated April 2019 values for CPI categories absent from the original source row.|
|`Imported Oil price index`|Monthly imported crude-oil price index and percentage changes used in Analysis 5.|

## Data Preparation and Missing Values

The original CPI data is retained separately from the prepared data. Power Query is used to organise the records and prepare the Rural+Urban series for analysis.

### Linear interpolation for April and May 2020

Where April and May 2020 values are missing between known March and June observations, linear interpolation estimates the missing values by dividing the change between the endpoints into three equal intervals:

* **April estimate:** March value + ((June value − March value) / 3)
* **May estimate:** March value + ((June value − March value) × 2 / 3)

For a single missing month between two known values, the midpoint is estimated as the average of the preceding and succeeding observations.

These estimates are documented in the `Null imputation` sheet and used to fill the corresponding missing values in the prepared Rural+Urban dataset. Linear interpolation assumes a constant change between known observations; imputed values are estimates, not official published observations.

### Estimating April 2019

April 2019 is missing from the original CPI data. The `April19` support sheet estimates each category's April value by averaging the March and May 2019 values:

`April 2019 estimate = AVERAGE(March 2019 value, May 2019 value)`

For example, the General Index estimate is:

`AVERAGE(140.4, 142.0) = 141.2`

The estimated row is incorporated into the prepared dataset for analyses that require the missing month. The original source data is retained separately, and the estimated row should be interpreted as imputed rather than observed data.

## Analytical Methods

### Annual inflation — Analysis 2

Annual-average inflation is calculated from the annual average General Index:

`((Current year's average index / Previous year's average index) - 1) × 100`

The workbook's displayed comparison covers 2017–2022, with 2016 used as the prior-year baseline.

### Month-on-month change — Analysis 3 and Analysis 5

Monthly percentage change is calculated as:

`((Current month's index / Previous month's index) - 1) × 100`

Analysis 3 applies this to Food and Beverages CPI. Analysis 5 applies it to imported crude-oil prices and selected CPI categories over the overlapping period from January 2021 to May 2023.

### Year-on-year inflation — Analysis 4

Year-on-year inflation compares an index with the same month in the previous year:

`((Current month's index / Same month's index in previous year) - 1) × 100`

Analysis 4 groups observations into the periods defined in the worksheet:

* **Pre-COVID:** January 2018–February 2020
* **COVID Onset:** March 2020
* **Post-COVID:** April 2020–March 2021

The period summaries report average YoY inflation for Food and Beverages, Fuel and Light, Health, Transport and Communication, and the General Index.

### Correlation — Analysis 5

Excel's `CORREL` function is used to calculate the Pearson correlation coefficient between the monthly percentage changes in imported crude-oil prices and the monthly percentage changes in each CPI category.

Correlation ranges from −1 to +1:

* Positive values indicate that changes tended to move in the same direction.
* Negative values indicate that changes tended to move in opposite directions.
* Values close to zero indicate little linear association in the selected sample.

Correlation does not demonstrate causation.

## Key Findings

### Analysis 1 — Selected CPI category shares

For May 2023, Pan, Tobacco and Intoxicants has the largest share among the eight selected CPI category values in each sector:

* **Rural:** approximately 13.62%
* **Urban:** approximately 14.21%
* **Rural+Urban:** approximately 13.82%

These percentages are shares of the selected index values, not official CPI expenditure weights or weighted contributions to inflation.

### Analysis 2 — Annual inflation

The annual-average General Index comparison shows that **2022 has the highest inflation rate in the displayed 2017–2022 period, at approximately 6.62%**. The rate is calculated from annual-average index values rather than from a single month's YoY change.

### Analysis 3 — Food CPI movements

From June 2022 to May 2023:

* October 2022 records the largest positive month-on-month Food and Beverages change in the displayed period, at approximately **1.01%**.
* December 2022 records the largest decline, at approximately **−1.35%**.
* Between June 2022 and May 2023, Spices shows the largest positive absolute index change among the listed food categories (**+30.9 index points**), while Oils and Fats shows the largest decline (**−30.9 index points**).

Absolute index-point changes should not be interpreted as weighted contributions to inflation.

### Analysis 4 — Inflation across COVID-related periods

The period summary shows different patterns across categories:

* **Transport and Communication** has the largest increase in average YoY inflation between the pre-COVID and post-onset periods, rising by approximately **6.94 percentage points**.
* Food and Beverages increases by approximately **1.51 percentage points**.
* Fuel and Light increases by approximately **1.31 percentage points**.
* The General Index increases by approximately **1.30 percentage points**.
* Health decreases by approximately **1.88 percentage points**.

These are comparisons between the periods defined in the workbook. They do not establish that COVID-19 alone caused the observed changes.

### Analysis 5 — Crude-oil and CPI correlations

The strongest positive correlations in the displayed results are:

* **Oils and Fats:** approximately **+0.441**
* **Meat and Fish:** approximately **+0.397**

The strongest negative correlations include:

* **Milk and Products:** approximately **−0.295**
* **Cereals and Products:** approximately **−0.287**

The correlations for Food and Beverages (**+0.017**) and the General Index (**+0.055**) are close to zero. Overall, the relationship between crude-oil price changes and CPI changes varies by category and is mostly weak to moderate in this sample.

## Limitations

* Some missing CPI values are estimated using linear interpolation; these values are not official observations.
* Linear interpolation assumes a uniform change between known observations and may not capture actual short-term price movements.
* The crude-oil analysis covers the overlapping monthly period from January 2021 to May 2023; results may differ for other periods.
* Correlation measures linear association and does not prove cause and effect.
* The Analysis 1 percentages describe shares of selected index values and should not be interpreted as official CPI weights.
* Results depend on the source data, date range, categories selected, and data-preparation choices.
* The 2023 CPI data in this workbook ends in May, so 2023 is not a complete calendar year for annual comparisons.

## How to Explore the Project

1. Open the Excel workbook and begin with `Raw CPI` to understand the source data.
2. Review `Cleaned CPI data` and `Rural+Urban Combined` to see the prepared data.
3. Review each Analysis sheet to explore calculations, summary tables, and charts.
4. Refer to `Null imputation` and `April19` to understand how missing observations were estimated.
5. Interpret the findings together with the limitations above.

## Conclusion

This project demonstrates an end-to-end Excel and Power Query workflow for preparing CPI data, estimating selected missing values, calculating inflation indicators, comparing category-level trends, and exploring the relationship between crude-oil price changes and CPI movements.

The analysis highlights differences in inflation patterns across categories and shows how transparent data preparation and clearly defined calculations support more interpretable results. The findings are descriptive and exploratory, and should be understood within the limitations of the selected data and methods.

## Project File

The repository should include the final Excel workbook:

`India CPI Inflation Analysis (2013-2023).xlsx`

## Author

Abhijeet Kumar Soni

Mail - abhijeetkumarsoni445@gmail.com




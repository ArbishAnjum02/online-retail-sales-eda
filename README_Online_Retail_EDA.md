# Exploratory Data Analysis on Online Retail Dataset

This project explores the Online Retail II dataset using Python. It focuses on cleaning transactional data, understanding product and customer purchasing patterns, and examining how transaction activity and sales value change across countries and months.

The analysis is carried out in a Jupyter Notebook using Pandas, NumPy, Matplotlib and Seaborn.

## Table of Contents

1. Overview
2. Problem Statement
3. Dataset
4. Tools and Technologies
5. Project Structure
6. Data Cleaning
7. Methods and Analysis
8. Key Insights
9. How to Run the Project
10. Results and Conclusion
11. Future Work
12. Author and Contact

## Overview

The notebook takes raw online retail transaction data through a cleaning process and exploratory data analysis. It examines quantity and price distributions, frequently recorded products, country-level activity, and monthly transaction trends.

A new `Total_Amount` feature is created by multiplying `Quantity` by `Price`. Log transformations are also applied to quantity and price to make their highly skewed distributions easier to inspect.

## Problem Statement

A large transaction dataset can be difficult to interpret without cleaning and summarising it first. This project explores the following questions:

1. What issues need to be handled before analysing the data?
2. How are quantity and unit price distributed?
3. Which products and stock codes appear most frequently?
4. Which countries contribute the most transaction records and transaction value?
5. How does transaction activity and total transaction value change by month?
6. Is there a clear relationship between quantity and unit price?

## Dataset

The notebook reads a local file named `online_retail_II.csv`.

The notebook's monthly chart covers December 2010 to December 2011. The fields used in the notebook include:

- `Invoice`
- `StockCode`
- `Description`
- `Quantity`
- `InvoiceDate`
- `Price`
- `Customer ID`
- `Country`

The dataset file is not included in this repository, so it needs to be downloaded or placed in the project folder before running the notebook.

## Tools and Technologies

- Python
- Jupyter Notebook
- Pandas
- NumPy
- Matplotlib
- Seaborn

## Project Structure

```text
online-retail-eda/
├── ONLINE RETAIL 2 EDA PROJECT(2).ipynb
├── online_retail_II.csv
└── README.md
```

The CSV file is the input dataset. Keep it in the same folder as the notebook, or update the file path in the data loading cell.

## Data Cleaning

The notebook includes the following cleaning steps:

1. Inspected the dataset structure, data types and summary statistics.
2. Checked missing values and duplicate records.
3. Removed rows with missing `Customer ID` values.
4. Standardised `StockCode` values by converting them to strings, trimming spaces and using uppercase.
5. Removed duplicate records.
6. Converted `InvoiceDate` to a datetime data type and converted `Customer ID` to a string-compatible format.
7. Created a cleaned dataset that keeps records with `Price` greater than 0 and below 5000, and `Quantity` greater than 0 and below 10000.

The final filtering step excludes records with zero or negative quantities, and records with zero or negative prices. This removes negative-quantity return records from the cleaned analysis, but the notebook does not explicitly filter invoices based on cancellation status.

## Methods and Analysis

### Univariate Analysis

- Examined the distribution and summary statistics of `Quantity` and `Price`.
- Compared mean and median values to understand the effect of extreme observations.
- Used `log1p()` transformations to reduce right skew and make the distributions easier to visualise.
- Reviewed the most frequently recorded product descriptions and stock codes.
- Compared the share of transaction records by country.
- Examined the number of records by month.

### Bivariate Analysis

- Compared stock codes by total quantity.
- Created `Total_Amount` by multiplying `Quantity` by `Price`.
- Compared total transaction amount across countries and product descriptions.
- Used log-transformed quantity and price in a scatter plot to inspect their relationship.
- Analysed monthly total transaction amount.
- Used a country-by-month heatmap to compare transaction record counts across selected countries.

## Key Insights

- The quantity distribution is strongly right-skewed. The mean quantity is higher than the median, indicating that a smaller number of large-quantity transactions affect the average.
- The original price distribution is extremely right-skewed. Applying `log1p()` reduces the skewness and makes the distribution easier to inspect.
- The United Kingdom accounts for the largest share of transaction records in the country analysis, so the overall patterns are heavily influenced by the UK market.
- `WHITE HANGING HEART T-LIGHT HOLDER` is the most frequent product description in the cleaned data, appearing 2,016 times. Frequency does not necessarily mean the product has the highest quantity sold or transaction value.
- Stock code `84077` has the highest total quantity among the stock codes shown in the quantity comparison.
- `REGENCY CAKESTAND 3 TIER` has the highest total transaction amount among the products shown in the product comparison.
- The notebook compares monthly record counts and monthly total transaction amounts. The trend should be interpreted in the context of the dataset's limited time coverage.
- December 2011 appears as a partial month in the dataset, so it should not be compared directly with complete months.
- The quantity and unit price scatter plot does not show a clear positive relationship between the two variables.

These findings describe the cleaned data and the visualisations in the notebook. Transaction counts, quantities and transaction amounts measure different things and should not be treated as interchangeable.

## How to Run the Project

1. Install Python and Jupyter Notebook, or use an environment that supports `.ipynb` files.
2. Install the required libraries:

```bash
pip install pandas numpy matplotlib seaborn jupyter
```

3. Place `online_retail_II.csv` in the same folder as the notebook.
4. Open the notebook in Jupyter Notebook or VS Code.
5. Run the cells in order, starting with the library imports and dataset loading cell.

The notebook currently loads the file using this path:

```python
df = pd.read_csv('online_retail_II.csv', encoding='latin1')
```

## Results and Conclusion

This project demonstrates a practical exploratory data analysis workflow, from checking data quality to visualising transaction patterns. It uses summary statistics and plots to investigate product activity, country-level records, transaction amounts and monthly trends.

The analysis also highlights important limitations. The cleaned data excludes non-positive quantities and prices, December 2011 is incomplete, and the dataset covers only about one year. The results therefore describe the transactions retained for this analysis and should not be treated as proof of recurring annual seasonality or overall business profitability.

## Future Work

- Compare average transaction value and spending per customer across countries.
- Analyse repeat purchasing using customer and invoice information.
- Investigate returns separately instead of excluding all non-positive quantities.
- Add more robust outlier checks and document the business reasoning behind each filter.
- Use multiple years of data to evaluate seasonality more reliably.
- Build a Power BI dashboard to present the main findings interactively.

## Author and Contact

**Author:** Arbish Anjum

**GitHub:** https://github.com/ArbishAnjum02

**LinkedIn:** Add your LinkedIn profile URL

**Email:** [arbishanjum3@gmail.com](https://mail.google.com/mail/?view=cm&fs=1&to=arbishanjum3@gmail.com)

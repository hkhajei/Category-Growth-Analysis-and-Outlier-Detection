# Category Growth Analysis and Outlier Detection

## Overview
This project analyzes category-level month-over-month (MoM) growth trends and detects statistical outliers in sales metrics (A, B, and C) for the year 2025. It processes historical data, computes growth rates, identifies outliers using the IQR method, and visualizes the results.

## Features
- Reads sales data from an Excel file (`Sample data.xlsx`).
- Aggregates data by `Category Group`, `Category`, `Year`, and `Month`.
- Computes month-over-month growth rates (`A Growth`, `B Growth`, `C Growth`).
- Detects outliers for the year 2025 based on historical data (2020-2024) using the interquartile range (IQR) method.
- Exports detected outliers to `category_MoM_outliers_2025.csv`.
- Generates visualizations comparing historical trends with 2025 projections and highlighting outliers.

## Installation & Requirements
Ensure you have Python installed along with the necessary libraries. You can install the dependencies using:
```bash
pip install pandas matplotlib numpy seaborn openpyxl
```

## Usage
1. Place the dataset file (`Sample data.xlsx`) in the same directory as the script.
2. Run the script:
   ```bash
   python script.py
   ```
3. The script will generate an output file `category_MoM_outliers_2025.csv`, containing detected outliers for 2025.
4. It will also generate visualizations of growth trends and outliers.

## Output
- **CSV File:** `category_MoM_outliers_2025.csv` listing outliers and reasons for classification.
- **Charts:**
  - Historical vs. 2025 trends for `A Growth`, `B Growth`, `C Growth`.
  - Scatter plots highlighting historical data, 2025 inliers, and outliers.

## Methodology
### 1. Data Aggregation
The script groups data by `Category Group`, `Category`, `Year`, and `Month` and computes sum aggregations for `A`, `B`, and `C`.

### 2. Growth Rate Calculation
Month-over-month growth rates for `A`, `B`, and `C` are calculated using:
```python
grouped['A Growth'] = grouped.groupby(['Category Group','Category'])['A'].pct_change()
```

### 3. Outlier Detection
The IQR method is used to identify outliers:
- Compute Q1 (25th percentile) and Q3 (75th percentile) from historical data (2020-2024).
- Calculate the lower and upper bounds:
  ```python
  lower_bound = Q1 - 1.5 * IQR
  upper_bound = Q3 + 1.5 * IQR
  ```
- Any 2025 data points falling outside this range are marked as outliers.

### 4. Visualization
- Line charts show historical trends and 2025 projections.
- Scatter plots highlight inliers and outliers for 2025.

## Example Output (CSV)
| Category | Year | Month | A Growth | B Growth | C Growth | Outlier Reason |
|----------|------|-------|----------|----------|----------|---------------|
| XYZ      | 2025 | 3     | -0.12    | 0.45     | 0.78     | A Growth too low |


##  Contact
For questions or feedback, reach out at:

- **Email**: [h.khajei@gmail.com](mailto\:.khajei@gmail.com)
- **GitHub**: [hkhajei](https://github.com/hkhajei)

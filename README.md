# Customer Segmentation & CLV Prediction

## Project Overview

This project focuses on customer segmentation and prediction of **Customer Lifetime Value (CLV)** using transactional data. It leverages **RFM analysis**, **predictive modeling**, and **data visualization** to help businesses understand customer behavior and take data-driven decisions to improve retention and value.

## Objectives

- Segment customers based on Recency, Frequency, and Monetary value (RFM).
- Predict Customer Lifetime Value (CLV) using machine learning.
- Classify customers into behavioral classes (High, Medium, Low Frequency).
- Generate actionable insights to improve marketing strategy and customer retention.

## Dataset

### Online Retail.csv

- Contains transactions from a UK-based online retailer from 2010–2011.
- Features include: `InvoiceNo`, `StockCode`, `Description`, `Quantity`, `InvoiceDate`, `UnitPrice`, `CustomerID`, and `Country`.

### classified_customers.csv (Generated)

Contains customer-wise aggregated data with predicted values and assigned segments:

| Column                          | Description                                   |
|--------------------------------|-----------------------------------------------|
| CustomerID                     | Unique ID of the customer                     |
| Recency                        | Days since last purchase                      |
| Frequency                      | Count of unique purchase occasions            |
| NumInvoices                    | Total invoices per customer                   |
| Monetary                       | Total revenue per customer                    |
| AvgOrderValue                  | Average value per transaction                 |
| AvgDaysBetweenPurchases        | Actual average days between purchases         |
| PredictedAvgDaysBetweenPurchases | ML model prediction                        |
| CustomerClass                  | Segmented class: High, Medium, or Low Frequency |

## Key Features & Workflow

### 1. Data Preprocessing

- Removed null or invalid `CustomerID` entries.
- Filtered out cancelled transactions.
- Handled outliers and calculated transaction value.

### 2. RFM Feature Engineering

- **Recency**: Days since last purchase.
- **Frequency**: Number of repeat purchases.
- **Monetary**: Total spending.

### 3. CLV Prediction

- Built a Random Forest Regressor to predict average days between purchases.
- Used Frequency, Monetary, Recency as features.
- Evaluated model using RMSE and prediction visualizations.

### 4. Customer Segmentation

- Applied custom rule-based classifier on predicted purchase frequency:
  - High Frequency: AvgDays < 30 days
  - Medium Frequency: AvgDays between 30–90 days
  - Low Frequency: AvgDays > 90 days

### 5. Visualization & Insights

- Bar plots, scatter plots, and histograms to analyze distribution and clustering.
- CLV prediction trends and customer class breakdowns.

## Tech Stack

- Python
- pandas, numpy
- matplotlib, seaborn
- scikit-learn

## Sample Output (classified_customers.csv)

```
CustomerID,Recency,Frequency,Monetary,...,CustomerClass
12347.0,1,7,4310.0,...,High Frequency
12363.0,109,2,552.0,...,Low Frequency
12410.0,300,3,681.07,...,Low Frequency
...
```

## Model Performance

- Model: Random Forest Regressor
- Evaluation Metric: RMSE (Root Mean Squared Error)
- Delivered strong predictive accuracy on purchase interval estimation.

## How to Run

1. Clone this repository or open the notebook in Jupyter/Colab.
2. Place the `Online Retail.csv` file in your working directory.
3. Run `Mlproject.ipynb` to:
   - Preprocess data
   - Train the model
   - Generate the output file `classified_customers.csv`

## Business Use-Cases

- **Customer Retention**: Target High and Medium Frequency users with personalized campaigns.
- **Resource Allocation**: Prioritize support/sales for high CLV segments.
- **Churn Prediction**: Identify customers with increasing inactivity patterns.

## Files Included

- `Mlproject.ipynb` – Jupyter notebook containing the full pipeline
- `Online Retail.csv` – Source dataset
- `classified_customers.csv` – Final output with CLV predictions and segmentation

## Credits

Dataset: [UCI Online Retail Dataset](https://archive.ics.uci.edu/ml/datasets/Online+Retail)  
Project by: *Sailendra Kumar*

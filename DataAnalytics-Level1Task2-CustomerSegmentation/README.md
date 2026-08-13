# Customer Segmentation Analysis

## Project Overview

This project applies machine learning clustering techniques to segment an e-commerce customer base based on purchasing behavior. The goal is to identify customer groups that can support targeted marketing strategies.

## Dataset

The dataset contains retail transaction information including:

- Customer ID
- Purchase Date
- Gender
- Age
- Product Category
- Quantity
- Price per Unit
- Total Amount

## Methodology

The project workflow included:

- Data inspection
- Data cleaning
- RFM analysis
- Feature scaling using StandardScaler
- K-Means clustering
- Elbow Method evaluation
- Customer segment profiling
- Business recommendations

## RFM Features

The following behavioral features were created:

- Recency: Days since the customer's last purchase
- Frequency: Number of purchases
- Monetary: Total customer spending

## Machine Learning Model

Algorithm used:

- K-Means Clustering

The Elbow Method was used to determine the optimal number of clusters.

## Customer Segments

### Cluster 0 — Inactive / Low-Value Customers
Recommendation:
- Use win-back campaigns and discounts.

### Cluster 1 — Recent Customers
Recommendation:
- Encourage loyalty and repeat purchases.

### Cluster 2 — High-Value Customers
Recommendation:
- Provide VIP experiences and exclusive offers.

## Tools Used

- Python
- Pandas
- NumPy
- Scikit-learn
- Matplotlib
- Seaborn
- Jupyter Notebook

## Visualizations

Project visualizations include:

- Elbow Method chart
- Customer cluster scatter plots
- Customer distribution by cluster

## Conclusion

Customer segmentation allows businesses to identify different customer behaviors and create personalized marketing strategies. By targeting each segment appropriately, companies can improve retention, customer satisfaction, and revenue growth.
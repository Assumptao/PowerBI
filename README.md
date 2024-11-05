# PowerBI
# Sales Order Analysis Dashboard

## Table of Contents
1. [Project Overview](#project-overview)
2. [Dataset](#dataset)
3. [Key Insights and Metrics](#key-insights-and-metrics)
4. [Dashboard Components](#dashboard-components)
5. [Data Preparation and Modeling](#data-preparation-and-modeling)
6. [Calculated Measures](#calculated-measures)
7. [Visualizations](#visualizations)
8. [Setup Instructions](#setup-instructions)
9. [Conclusion](#conclusion)
    
## Project Overview
This Power BI project provides an in-depth analysis of sales order data, focusing on key performance metrics such as revenue, profit, order quantity, and delivery times. The goal is to gain insights into channel performance, customer trends, and sales efficiency to make data-driven business decisions.

*Sample dashboard screenshot:*
![Dashboard Screenshot](images/dashboard.png) <!-- Replace with the actual path to your image -->

## Dataset
The analysis is based on a dataset containing sales orders and related details. The dataset includes fields like:
- **Order ID**: Unique identifier for each order
- **Order Date**: Date the order was placed
- **Channel**: Sales channel (e.g., online, in-store)
- **Order Quantity**: Quantity of items in the order
- **Total Revenue**: Revenue generated by each order
- **Total Unit Cost**: Unit cost for items in the order

> **Note:** Specify the source of your data or mention that it's simulated if it's not from a real source.

## Key Insights and Metrics
Here are some of the main insights and metrics derived from the analysis:
- **Total Profit**: 57.79M
- **Total Revenue**: 154.57M
- **Total Orders**: 7,991
- **Average Delivery Days**: 60.08 days

These metrics provide a snapshot of the overall sales performance and efficiency.

## Dashboard Components
The Power BI dashboard contains multiple visualizations, including:
- **Revenue and Order Trends by Month**: Visualizes monthly trends in total revenue and order volume.
- **Orders and Revenue by Channel**: Compares performance across different sales channels.
- **Quantity Sold vs. Total Revenue**: Analyzes the relationship between quantity sold and total revenue.
- **Profitability by Channel**: Identifies the most profitable sales channels.

## Data Preparation and Modeling
The dataset underwent several steps of data preparation, including:
1. **Data Cleaning**: Removing duplicates, handling missing values, and standardizing date formats.
2. **Table Creation**: Creating tables for sales orders, channels, and date information.
3. **Data Transformation**: Calculating new columns for profit, delivery days, and other derived metrics.
4. **Relationships**: Establishing relationships between tables (e.g., linking sales orders to date and channel tables).

### Data Model
Here's an overview of the data model used in the project:

![Data Model Screenshot](images/data_model.png) <!-- Replace with the actual path to your image -->

## Calculated Measures
Several DAX measures were created to provide additional insights. Some key measures include:

- **Total Revenue**
  ```DAX
  Total Revenue = SUM('Sales Orders - Fact'[Total Revenue])
- **Total Profit**
  ```DAX
  Total Profit = SUMX('Sales Orders - Fact', [Total_Revenue] - 'Sales Orders - Fact'[Order Quantity]*'Sales Orders - Fact'[Total Unit Cost]) 
- **Order Quantity**
  ```DAX
  Order Quantity = SUM('Sales Orders - Fact'[Order Quantity])
- **Average Delivery Days**
  ```DAX
  Average Delivery Days = AVERAGE('Sales Orders - Fact'[Delivery Days])



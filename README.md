## Sales Order Analysis 

### Table of Contents

- [Project Overview](#project-overview)
- [Dataset Source](#dataset-source)
- [Tools Used](#tools-used)
- [Data Cleaning/Preparation](#data-cleaningpreparation)
- [Data Modeling](#data-modeling)
- [Exploratory Data Analysis (EDA)](#exploratory-data-analysis-eda)
- [Data Analysis](#data-analysis)
- [Calculated Measures and Columns](#calculated-measures-and-columns)
- [Visualization](#visualization)
- [Results/Findings](#resultsfindings)
- [Key Insights and Metrics](#key-insights-and-metrics)
- [Recommendations](#recommendations)

### Project Overview

This Power BI project provides an in-depth analysis of sales order data, focusing on key performance metrics such as revenue, profit, order quantity, and delivery times. The goal is to gain insights into channel performance, customer trends, and sales efficiency to make data-driven business decisions.

*Dashboard Screenshot:*![powerbi project](https://github.com/user-attachments/assets/bf02e911-b115-482c-8ca3-0b3c1aef8628)

## Dataset Source

The Primary dataset used for this analysis is the "Sales Order.xlxs" file containing sales orders and other metrics. The dataset consisted of 12 columns and over 7991 rows with fields like

- **Order Number**: Unique identifier for each order
- **Order Date**: Date the order was placed
- **Channel**: Sales channel (e.g.,Ware house, wholesale,Distributor)
- **Order Quantity**: Quantity of items in the order
- **Total Revenue**: Revenue generated by each order
- **Total Unit Cost**: Unit cost for items in the order

> **DATASET:** (https://drive.google.com/file/d/1z77RuKqBwitGfXyjiQ1lALx4sTSFSaws/view?usp=drive_link)

### Tools Used

- Power Query - Data Cleaning
- Power BI - Creating Reports

### Data Cleaning/Preparation:

#### Initial cleaning was done in Power Query:
 
  - Renamed fields for clarity; Customer Name Index to Customer ID,Delivery Region ID was changed to Delivery ID as well as Products Description Index to Product DescriptionID.
  - Removed unnecessary columns; Currency Code column was removed
  - Replaced missing values where necessary, using the median for numerical fields to maintain data integrity

### Data Modeling:
  - Created fact and dimension tables:
  - A fact table is a table that contains all the primary key of the dimension table and the associated metrics. Dimension Table contains the primary keys of that table and the description of the metrics in the fact table.
  - Renamed the Sales Orders Table to Sales Orders-Fact
  - Duplicated the Sales Order-Fact Table twice and renamed as Channel –Dim and Warehouse - Dim, (they are the categorical data in the dataset)
  - In the channel –Dim Table, other columns except the channel column were deleted, duplicate from the column were removed, then a column index was created - this is the unique ID for channel. (click on Add column tab; click on the drop down for index column, click FROM 1) ,do same for Warehouse - Dim
    - `Sales Orders-Fact` (central fact table)
    - `Channel-Dim` and `Warehouse-Dim` (dimension tables)
  - Established relationships between tables using Primary and Foreign Keys to enable data normalization and integrity.
  - **Joins (merge)**: Used Left Outer Joins to combine tables based on common fields (Channel and Warehouse).

Here's an overview of the data model used in the project:

![model](https://github.com/user-attachments/assets/6dc97f71-0454-4160-90a9-cb52b4d27969)

### Exploratory Data Analysis (EDA)

EDA involves exploring dataset to answer key questions like:

1. What is the Total Profit?
2. What is the Total Revenue?
3. How many orders were generated?
4. What is the Average Delivery date?
   
### Data Analysis

#### Calculated Measures and Columns

##### Several DAX measures were created to provide additional insights. Some key measures include:

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

### Visualization

The dashboard includes several visuals to display sales metrics, trends, and channel performance:

1. **Total Revenue by Month (Line Chart)** – Tracks revenue patterns over the year.
2. **Order Quantity by Month (Bar Chart)** – Displays monthly order quantity distribution.
3. **Orders by Month (Line Chart)** – Illustrates the frequency of orders over time.
4. **Total Revenue by Channel (Pie Chart)** – Breaks down revenue by channel (Wholesale, Distributor, Export).
5. **Orders by Channel (Funnel Chart)** – Visualizes order distribution across different channels.
6. **Quantity Sold by Total Revenue (Scatter Plot)** – Shows the relationship between quantity sold and total revenue.
7. **Total Profit by Channel (Heat Map)** – Highlights profitability for each channel.

### Results/Findings

#### Key Insights and Metrics

Here are some of the main insights and metrics derived from the analysis:
- **Total Profit**: 57.79M
- **Total Revenue**: 154.57M
- **Total Orders**: 7,991
- **Average Delivery Days**: 60.08 days

1. Top Channels: Distributor leads in revenue (82.97M), while wholesale is most profitable (30.73M).
2. Seasonal Peak: Orders and revenue peak around July-August, reaching ~15M monthly.
3. Growth Opportunity: Export channel is lowest in revenue (22.64M) and profit (8.63M).

### Recommendations
Based on the analysis, I recommend the following;

- Prioritize Distributor and Wholesale Channels: Focus resources here, as they bring the highest revenue and profit.
- Prepare for Seasonal Peaks: Increase inventory and staffing around July-August to meet higher demand.
- Grow Export Channel: Explore new markets or targeted marketing to boost export performance.
- Reduce Delivery Time: Streamline logistics to improve customer satisfaction.
- Monitor Monthly Trends: Regularly assess trends to stay agile and adjust strategies as needed.







# E-Commerce Sales Dashboard  
**Project Domain: Business Analytics / E-Commerce**

This repository contains an interactive Power BI dashboard that provides deep insights into online sales performance. The dashboard enables businesses to track and analyze key metrics like revenue, profit, customer demographics, product performance, and payment methods over various time periods and locations. The relationship between the data tables is modeled as **one-to-many**, allowing a comprehensive view of sales at different levels of granularity.

**[Checkout E-Commerce Sales Dashboard](https://app.powerbi.com/view?r=eyJrIjoiODYyYjM4YTgtMjVmYy00YzY2LWFmN2MtM2QwZDdjMjI4YWI4IiwidCI6ImRmODY3OWNkLWE4MGUtNDVkOC05OWFjLWM4M2VkN2ZmOTVhMCJ9&embedImagePlaceholder=true)**


## Overview  
The **E-Commerce Sales Dashboard** visualizes various key performance indicators (KPIs) and allows users to explore data through dynamic filtering. It supports detailed insights on total sales, profit, and order quantity, as well as top-performing states, customers, and product categories.

### Key Features:
- **Sales Metrics**: Displaying total **Sales Amount**, **Profit**, **Quantity Sold**, and **Average Order Value (AOV)**.  
  *AOV = Amount ÷ Quantity* (Calculated using DAX).
- **State and Region Insights**: A breakdown of sales performance by state (e.g., Madhya Pradesh, Maharashtra) and their contributions to overall revenue.
- **Category and Sub-Category Performance**: Analysis of product categories like Electronics, Clothing, and Furniture, with deeper insights into sub-categories.
- **Payment Mode Distribution**: Visualization of sales by payment methods such as UPI, COD, debit cards, credit cards, and EMI.
- **Top Consumers**: A chart showing the top customers based on total purchases.
- **Monthly Profit-Loss Trend**: A monthly breakdown of profit and loss, helping identify sales patterns throughout the year.
- **Interactive Filters**: Users can filter data by **quarter** and **state** for more focused insights.

## Data Structure  
The dashboard uses two datasets, related through a **one-to-many** relationship on the `Order ID` field:

1. **Details Table**:
   - `Order ID`: Unique identifier for each transaction.
   - `Amount`: The total value of the order.
   - `Profit`: Profit made from the order.
   - `Quantity`: Number of items in the order.
   - `Category`: Broad category of the purchased items (e.g., Electronics, Clothing).
   - `Sub-Category`: Specific sub-categories within the product category (e.g., Electronic Games).
   - `PaymentMode`: Mode of payment used (e.g., COD, UPI).

2. **Orders Table**:
   - `Order ID`: Unique identifier for each order, linked to the Details table.
   - `Order Date`: The date on which the order was placed.
   - `Customer Name`: Name of the customer who placed the order.
   - `State`: State where the order was placed (used for regional analysis).
   - `City`: City where the customer is located.

The **one-to-many** relationship between these tables allows for seamless analysis across different dimensions, such as product categories and geographical regions.

### Relationship Model:
- **One-to-Many**:  
  - `Orders[Order ID]` (Primary Key)  
  - `Details[Order ID]` (Foreign Key)  
  This relationship connects each order to its detailed information, enabling aggregated calculations and filtering in the Power BI dashboard.

## DAX Calculation for Average Order Value (AOV):
To calculate **AOV**, the following DAX formula is used:

```DAX
AOV = DIVIDE(SUM(Details[Amount]), SUM(Details[Quantity]))
```

This formula divides the total sales amount by the total quantity of items sold, providing a metric that represents the average order value per transaction.

Additionally, the following DAX query retrieves the top 100 orders based on sales amount:

```DAX
EVALUATE
    TOPN(100, 'Details')
```

## Project Learnings  
- Successfully created a **one-to-many relationship** model in Power BI to combine sales order data with detailed transactional data.
- Developed a dynamic, interactive dashboard with drill-down capabilities using **Power BI filters** and **slicers**.
- Created custom measures using **DAX** to compute important KPIs like **Average Order Value (AOV)**.
- Visualized multiple types of data using bar charts, pie charts, donut charts, and line charts to represent different sales metrics, product performance, and regional insights.
- Applied advanced data manipulation techniques for analyzing sales across different product categories, states, and customer segments.

## Dashboard Snapshot
![Dashboard](https://github.com/user-attachments/assets/abc4bd0c-554c-4237-a8d0-fd5123b6a6ff)

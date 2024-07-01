## Steps to Implement

### Step 1: Load Data

1. **Load Data**: Load the sales data into Tableau Desktop from an Excel file or SQL server connection.

### Step 2: Create Dashboard Components

1. **Create Sheets**: Create seven sheets for different visualizations.

### Step 3: Create YTD Total Sales KPI

1. **Name a Sheet**: Create a new sheet named **YTD Total Sales**.
2. **Dynamic KPI Calculation**:
    ```sql
    SUM(IF 
    YEAR([Date]) = {FIXED : MAX(YEAR([Date]))}
    THEN
    [Price ($)]
    END)
    ```
3. **Convert to Currency**: Format the value as currency and adjust text alignment.
4. **Drag into Text**: Drag **YTD Total Sales** into the text.

### Step 4: Create YOY Sales Growth KPI

1. **Duplicate Sheet**: Duplicate **YTD Total Sales** and rename it **PYTD Total Sales**.
2. **Edit Calculation for Previous Year**:
    ```sql
    SUM(IF 
    YEAR([Date]) = {FIXED : MAX(YEAR([Date]))}-1
    THEN
    [Price ($)]
    END)
    ```
3. **Create YOY Sales Growth Calculation**:
    ```sql
    ([YTD Total Sales] - [PYTD Total Sales])
    / [PYTD Total Sales]
    ```
4. **Drag into Text**: Drag **YoY Sales Growth** into the text.

![image](https://github.com/VinayMaddineni25/Car_Sales_Dashboard_Tableau_Project/assets/71554745/a13e22b3-6b12-430c-ae81-e5e8ba711881)

### Step 5: Create YTD Cars Sold KPI

1. **Create Sheet**: Name a new sheet **YTD Cars Sold**.
2. **Calculation**:
    ```sql
    COUNT(IF
    YEAR([Date]) = {MAX(YEAR([Date]))}
    THEN
    [Car id]
    END)
    ```

### Step 6: Create YOY Cars Sold Growth KPI

1. **Duplicate Sheet**: Duplicate **YTD Cars Sold** and rename it **PYTD Cars Sold**.
2. **Edit Calculation for Previous Year**:
    ```sql
    COUNT(IF
    YEAR([Date]) = {MAX(YEAR([Date]))}-1
    THEN
    [Car id]
    END)
    ```
3. **Create YOY Cars Sold Growth Calculation**:
    ```sql
    ([YTD Cars Sold] - [PYTD Cars Sold]) / [PYTD Cars Sold]
    ```
4. **Drag into Text**: Drag both **YTD Cars Sold** and **YoY Cars Sold** into the text.

![image](https://github.com/VinayMaddineni25/Car_Sales_Dashboard_Tableau_Project/assets/71554745/0e0947f4-e113-4957-84e2-c6cf21274352)

### Step 7: Create YTD Average Price KPI

1. **Create Sheet**: Name a new sheet **YTD Avg Price**.
2. **Calculation**:
    ```sql
    [YTD Total Sales] / [YTD Cars Sold]
    ```

### Step 8: Create YOY Average Price Growth KPI

1. **Calculate PYTD Avg Price**:
    ```sql
    [PYTD Total Sales] / [PYTD Cars Sold]
    ```
2. **Create YOY Avg Growth Calculation**:
    ```sql
    ([YTD Avg Price] - [PYTD Avg Price]) / [PYTD Avg Price]
    ```
3. **Drag into Text**: Drag both **YTD Avg Price** and **YoY Avg Growth** into the text.

![image](https://github.com/VinayMaddineni25/Car_Sales_Dashboard_Tableau_Project/assets/71554745/d9540af0-0732-4310-922f-df7c52740a71)

### Step 9: Create YTD Sales Weekly Trend

1. **Create Sheet**: Name a new sheet **YTD Sales Weekly Trend**.
2. **Apply WEEK(Date)**: Use `WEEK([Date])` in columns, select continuous, and drag **YTD Total Sales** into rows.
3. **Adjust Chart**: Convert to an Area chart, drag **YTD Total Sales** into rows again, synchronize, and convert the second marks to a line chart. Adjust transparency, labels, and colors.

![image](https://github.com/VinayMaddineni25/Car_Sales_Dashboard_Tableau_Project/assets/71554745/87ae2c36-962f-40b2-9368-d3b60f6b6eae)

### Step 10: Create YTD Total Sales by Body Style

1. **Create Sheet**: Name a new sheet **YTD Total Sales by Body Style**.
2. **Pie Chart**: Change Marks to Pie chart, drag Body Style to colors and labels, and **YTD Total Sales** to angle and label. Format accordingly.

![image](https://github.com/VinayMaddineni25/Car_Sales_Dashboard_Tableau_Project/assets/71554745/961b1614-9c90-4074-a855-d95f7a1c0383)

### Step 11: Create YTD Total Sales by Color

1. **Create Sheet**: Name a new sheet **YTD Total Sales by Color**.
2. **Pie Chart**: Change Marks to Pie chart, drag Color to colors, and **YTD Total Sales** to angle and label. Create two instances in row, right-click on one instance, select dual axis, remove everything from the second marks, and adjust sizes.

![image](https://github.com/VinayMaddineni25/Car_Sales_Dashboard_Tableau_Project/assets/71554745/25466c7b-c7c1-46ca-b3eb-5e16ce3d7f74)

### Step 12: Create YTD Cars Sold by Dealer Region

1. **Create Sheet**: Name a new sheet **YTD Cars Sold by Dealer Region**.
2. **Bar Chart**: Drag Dealer Region to rows, **YTD Total Sales** to columns, and Transmissions to colors. Sort in descending order, add labels, and format.

![image](https://github.com/VinayMaddineni25/Car_Sales_Dashboard_Tableau_Project/assets/71554745/9332b38a-d573-4fed-84d1-0570917ecc2d)

### Step 13: Create Company-Wise Sales Trend

1. **Create Sheet**: Name a new sheet **Company-Wise Sales Trend**.
2. **Trend Analysis**: Drag Company to rows, double-click on **YTD Avg Price**, **YTD Cars Sold**, and **YTD Total Sales**. Adjust percentages and decimals, arrange rows and columns, and format colors.

![image](https://github.com/VinayMaddineni25/Car_Sales_Dashboard_Tableau_Project/assets/71554745/c2e22a4b-4dbe-4416-8ad9-e240d9b574ae)

### Step 14: Arrange Dashboard

1. **Arrange KPIs and Charts**: Arrange all KPIs and charts in the designed dashboard and format shapes, sizes, and colors accordingly.

![Slide1](https://github.com/VinayMaddineni25/Car_Sales_Dashboard_Tableau_Project/assets/71554745/950369a0-2f7b-437c-99da-d2896fa566ab)


## Insights

### Overview

This Car Sales Dashboard provides a comprehensive view of key performance indicators (KPIs) related to our car sales data. It allows for real-time monitoring of sales metrics, trends, and performance across different dimensions such as time, body style, color, and dealer regions.

### Visualizations

1. ** YTD Sales Weekly Trend: Display a line chart illustrating the weekly trend of YTD sales. The X-axis should represent weeks, and the Y-axis should show the total sales amount.

2. **YTD Total Sales by Body Style: Visualize the distribution of YTD total sales across different car body styles using a Pie chart.

3. **YTD Total Sales by Colour: Present the contribution of various car colours to the YTD total sales through a donut chart.

4. **YTD Cars Sold by Dealer Region: Showcase the YTD sales data based on different dealer regions using a bar chart to visualize the sales distribution geographically.

5. **Company-Wise Sales Trend in Grid Form: Provide a tabular grid that displays the sales trend for each company. The grid should showcase the company name along with their YTD sales figures.

![image](https://github.com/VinayMaddineni25/Car_Sales_Dashboard_Tableau_Project/assets/71554745/fb84e84c-10fe-4995-8ee9-c25767667300)

## Summary

The Car Sales Dashboard provides valuable insights into the current sales performance, highlighting significant growth in total sales and the number of cars sold. Despite a slight decrease in the average price, the overall sales trend is positive. The visualizations offer a clear view of sales distribution by body style, color, dealer region, and company, helping to identify key trends and areas of strength. This comprehensive dashboard is an essential tool for informed decision-making and strategic planning in the car sales industry.

1. Data Cleaning and Transformation:
•	Removed zero and negative values from sales amounts.
•	Converted currency from USD to INR in sales amounts. A conditional column was added using the formula:
 `= Table.AddColumn(#"Filtered Rows", "norm_sales_amount", each if [currency] = "USD" then [sales_amount]*75 else [sales_amount])`.

3. Base Measure Table:
•	Created a base measure table with a new measure called "Revenue" using the formula: `Revenue = SUM('sales transactions'[sales_amount])`.
•	Added another measure called "Sales Quantity" using the formula: `Sales Qty = SUM('sales transactions'[sales_qty])`.

4. Data Visualization:
•	Created a visual showing revenue by the customer with data labels enabled to display revenue for each customer.
•	Created a visual for sales quantity by customer.
•	Tracked revenue numbers by year and added a slicer to filter data by year.
•	Added a slicer to filter data by month.
•	Created a visual for revenue by region, allowing for revenue analysis by region. For example, in 2020, Chennai generated 2.46 million out of 142.22 million
  in revenue. 
  This data can be verified using the following SQL formula:
 `SELECT SUM(transactions.sales_amount) FROM transactions INNER JOIN date ON transactions.order_date=date.date WHERE date.year=2020 AND transactions.market_code="Mark001";`. (Where "Mark001" is the code for Chennai.)

5. Top 5 Analyses:
•	Applied a top 5 filter to track the top 5 customers in the revenue by customer name filter. Select the visual, go to the filters pane, select filter by top 5,
  add revenue in "By value," and apply changes.
•	Applied a top 5 filter to track the top 5 products.

6. Revenue Trend Visualization:
Created a line chart visualizing revenue trend over time. Revenue is plotted on the Y-axis, and dates are plotted on the X-axis.

7. Settings and Integration:
•	Changed default visual interaction from cross-highlighting to cross-filtering under *File > Option and Settings > Options > Report Settings.
  This change ensures that irrelevant bars in the visual will be hidden.
•	Integrate the dashboard into the main webpage or mobile applications for easy access by AtliQ hardware directors, enabling quick insights into the business.

Outcome: Previously, the company invested significant resources in building dashboards and web applications, involving engineering teams and incurring significant 
costs and time. Now, data analysts can efficiently create and integrate dashboards, allowing company directors to quickly access and assess business performance.

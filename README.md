# Sales Quarterly Performance Optimization and Insights Dashboard for Maven Technology

# Project Overview
## Background:
Maven Technology is a B2B company specializing in selling computer hardware to large-scale businesses. They have recently integrated a CRM system to track their sales opportunities. However, sales managers and other stakeholders currently lack visibility into the data for performance insights outside of the CRM. In their quest to become a fully data-driven organization, Maven Technology is looking to implement an interactive dashboard. This dashboard will allow sales managers to monitor their teams' performance on a quarterly basis, providing crucial insights that will enable them to make informed decisions and improve their sales processes.

## Objectives:
The project aims to utilize the sales data to generate actionable insights that will enable Maven Technology's management team to:

- Evaluate Team Performance: Analyze how each sales team is performing compared to others, identifying both high and low performers.
- Sales Agent Analysis: Identify if any sales agents are lagging in performance and require support or training.
- Trend Analysis: Detect quarter-over-quarter trends in sales performance, helping to predict future outcomes and adjust strategies accordingly.
- Product Performance: Determine if certain products or series have higher win rates, guiding future focus and promotional efforts.
- Sector Demand: Identify which sectors are purchasing products more frequently, allowing Maven Technology to refine their target strategies for maximum growth.

## Key Questions:
The following critical questions will guide the project and help meet the company's strategic goals:

1. How is each sales team performing compared to the rest?
2. Are any sales agents underperforming, and if so, who are they?
3. Can we identify trends in sales performance quarter-over-quarter?
4. Which products are showing the highest win rates?
5. Which sectors are driving the greatest demand for Maven Technology's products?

# Data Description
The dataset was obtained from Maven Analytics. It comprises four primary tables containing information about accounts, products, sales teams, and the sales pipeline. The sales pipeline consists of approximately 8,800 rows and 8 columns, which will be integrated with the other tables for comprehensive analysis.

1. Account Table:
   - Account: The name of the company purchasing the products.
   - Sector: The industry of the purchasing company.
   - Year Established: The year the company was founded.
   - Revenue: The annual revenue of the company.
   - Employee: The number of employees in the company.
   - Office Location: The headquarters of the company.
   - Subsidiary of: The parent company of the account, if applicable.

2. Product Table:
   - Products: The name of the product.
   - Series: The series or category to which the product belongs.
   - Sales Price: The suggested retail price of the product.

3. Sales Team Table:
   - Sales Agent: The name of the sales representative.
   - Manager: The sales agent’s direct manager.
   - Regional Office: The office or branch where the sales team is based.

4. Sales Pipeline Table:
   - Opportunity ID: A unique identifier for each sales opportunity.
   - Sales Agent: The agent handling the sales opportunity.
   - Product: The product being sold.
   - Account: The name of the company purchasing the product.
   - Deal Stage: The current stage in the sales pipeline (prospecting > engaging > won > lost).
   - Engage Date: The date the deal entered the 'Engaging' stage.
   - Close Date: The date the deal was either won or lost.
   - Close Value: The revenue generated from the sale if the deal is won

# Data Normalization
The sales pipeline table, dated between October 2016 to December 2017, contains approximately 1,425 missing values in the account column, which were left as empty spaces. The following data cleaning processes were carried out on the data.

- Standardized the product name by replacing "GTXPro" with "GTX Pro" in the sales pipeline table.

- Used the first row as headers in the sales teams table for proper column alignment.

- Added an "account age" column to the accounts table, and changed its data type to a whole number for accurate representation.

- Added a "days to close" column in the sales pipeline table to track the number of days it took for deals to close.

- Renamed the "sector" column in the accounts table to proper case using a custom column for consistency in formatting.


# Merging Queries
I merged the sales pipeline table with the products table using an inner join on the product column, resulting in a new query named "CRM Sales." The newly added columns were renamed and repositioned for clarity. Next, the CRM Sales table was merged with the sales teams table, again using an inner join on the sales agent column. The newly added columns were also renamed and repositioned. The CRM Sales table was not merged with the accounts table due to the missing values in its account column, which could impact key analyses such as total potential sales. Rather, I chose to create a relationship between the two tables.

# Data Modeling
For data modeling, two date tables were added—one for the engage date and one for the close date. These tables were joined to the CRM Sales table using a one-to-many cardinality on their respective date columns. Additionally, the accounts table was connected to the CRM Sales table using the account column, also with a one-to-many cardinality. This structured approach ensures clean data, accurate relationships, and optimized performance for downstream analysis and reporting.

# Dashboard Design Thinking
When designing the dashboard for this analysis, the primary focus was on creating a user-friendly, interactive interface that enables managers to quickly access key insights and trends for their team. The design emphasizes clarity, efficiency, and the ability to drill down into more detailed views when necessary. Here are the design considerations for the overall Layout:

- Top-level summary section: The dashboard begins with a high-level summary that provides key performance indicators (KPIs) such as total sales revenue, average days to close, the number of won deals, and discounted sales percentage. This section will allow users to grasp the most critical metrics at a glance.

- Slicers: Interactive slicers are positioned prominently to allow users to drill down by the team manager. 

- Information Page: An information page was provided to help managers navigate the dashboard, for those who aren't familiar with power bi business intelligence tool. Also, the page defines key metrics to avoid assumptions and confusions. 

- Main Visuals: The dashboard will be divided into multiple visual elements that focus on different aspects of the data: such as the overview page, sales performance page, manager performance page, product performance page, and the lead performance analysis page. These visuals should support both aggregated and detailed views to assist in identifying actionable insights.

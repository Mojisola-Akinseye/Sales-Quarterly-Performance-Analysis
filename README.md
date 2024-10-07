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
   - Close Value: The revenue generated from the sale if the deal is won.



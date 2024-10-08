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

# Descriptive Analysis
## Qquarter Overview Performance Page:

![CRM-Sales-2](https://github.com/user-attachments/assets/c07c8bc7-1252-414a-93a7-c8c772419888)

The overview page of the dashboard features a personalized welcome message that activates when a manager's name is selected. This personalization enhances the user experience, making it more engaging and easier for managers to navigate and explore the data. To streamline navigation, icons have been incorporated to provide quick access to different sections of the dashboard. This improves usability by enabling faster exploration of key insights, enhancing overall efficiency.

Custom DAX measures were developed to track critical KPIs such as total sales, average weeks to close, won deals, and discounted sales, focusing specifically on Q4 2017 performance. By isolating this quarter, the analysis offers a detailed view of recent performance, helping managers assess strengths and areas for improvement during that period.

Additionally, DAX measures were utilized to calculate quarter-over-quarter performance metrics, including percentage growth changes, visual growth trend icons, and color indicators. These visual cues allow managers to quickly assess performance trends, highlighting areas of growth or concern. Accompanying variance column charts display fluctuations across key metrics throughout 2017, allowing managers to spot patterns or anomalies that could inform strategic decisions.

A table summarizing sales agent performance across the various metrics is included to provide insight into individual contributions to the company’s success. This breakdown is essential for identifying top performers and pinpointing agents who may require additional support or training.

Lastly, a potential sales bar chart, powered by a DAX measure, has been added to help managers identify products with the most open opportunities for sales. This visualization assists in prioritizing products with high sales potential, enabling managers to allocate resources more effectively and focus on areas with the highest returns.

## Quarter Sales Performance Analysis Page:

![CRM-Sales-3](https://github.com/user-attachments/assets/b302e9be-ddf0-4733-b44b-55b856d08afd)

This page provides a comprehensive breakdown of total sales by sector and account, enabling managers to identify industries and accounts with the highest demand for their products. Understanding where the largest sales volumes originate allows for more effective resource allocation, strategic focus on high-demand sectors, and identification of growth opportunities in underperforming areas.

Additionally, a quarterly sales trend has been incorporated, along with details on quarter-over-quarter growth percentages. This metric highlights the rate of sales growth or decline between quarters, providing valuable insights into overall performance.

To further enhance visibility into the sales process, a stacked column chart illustrates the sales opportunity funnel from the engagement stage throughout the quarter. This visualization shows the progression of sales opportunities across various stages of the funnel (e.g., from engagement to closing). It allows managers to monitor how opportunities are advancing through the pipeline and identify potential bottlenecks. By focusing on stages where deals may be stalling, managers can implement strategies to improve the overall sales conversion rate.

## Manager Performance Analysis Page:

![CRM-Sales-4](https://github.com/user-attachments/assets/dced27bf-c26e-4671-b44a-68cdd02833f4)

This page provides a detailed overview of how a manager's team ranks against other teams. It measures team performance relative to peers, fostering healthy competition and helping identify strengths and areas for improvement. This analysis empowers managers to evaluate their team’s performance through the following key metrics:

- Total Sales: Assesses the team’s revenue contributions compared to others, offering insights into overall effectiveness.
- Total Won Deals: Evaluates the team’s success in closing deals, highlighting opportunities for growth and development.
- Average Weeks to Close: Reflects the efficiency of the sales cycle by comparing the time taken to close deals.
- Total Engaged Sales: Demonstrates the team’s proactive efforts in pursuing sales opportunities, showcasing their engagement level.
- Discounted Sales Percentage: Indicates the degree of reliance on discounts and its potential impact on profitability.
- Average Sales: Offers insights into deal values, revealing whether the team focuses on high-value transactions or a greater volume of smaller deals.

## Product Performance Analysis Page:

![CRM-Sales-5](https://github.com/user-attachments/assets/efc63d56-a8ce-40bb-9f76-cbc18a877164)

This page presents total sales by product for Q4, highlighting best-selling products and those that are underperforming. This insight enables the team to concentrate efforts on high-demand products. 

A scatter plot has been included to identify any potential relationship between the average time to close deals (in days) and total sales by product. A lack of correlation between these variables may indicate inefficiencies in the sales process, suggesting that longer closure times do not necessarily lead to higher sales. This points to potential wasted time and financial losses, underscoring the need for process improvements.

Additionally, a line chart displays the top three products by win rates throughout the quarter. A brief overview of each product's performance is provided based on key metrics such as sales, win rates, and time to close. This summary allows the team to quickly identify strengths and weaknesses across their product line, informing strategic decisions to enhance the performance of underperforming products while capitalizing on top sellers.

## Lead Performance Analysis Page:

![CRM-Sales-6](https://github.com/user-attachments/assets/7678eae9-627d-4c98-ad22-8825512eaf28)

A tornado chart has been included to illustrate the comparison of won versus lost deals by sector. This visual representation highlights which sectors are performing well and identifies areas where sales efforts may be lacking. It enables managers to focus on enhancing sales strategies in underperforming sectors.

Additionally, two tables have been provided to summarize concluded deals and potential sales opportunities. These tables offer a clear overview of closed deals and upcoming sales prospects, equipping managers with insights into past performance and future opportunities. This information aids in tracking success rates and identifying sectors or clients with untapped potential, facilitating more targeted sales efforts.

# Recommendation
## Leverage Quarterly Sales Trends: 
Utilize the quarterly sales trend data to forecast future sales and set realistic targets. Managers should regularly review these trends to assess the effectiveness of current sales strategies and make informed adjustments as needed.

## Enhance Focus on High-Demand Products: 
Utilize insights from the total sales data to prioritize marketing and sales efforts on best-selling products. Allocate additional resources to these products to maximize their potential and explore opportunities for upselling or cross-selling.

## Address Underperforming Products
Conduct a deeper analysis of the underperforming products to understand the reasons for low sales. Consider gathering feedback from the sales team and customers to identify barriers to sales, such as pricing, features, or market fit. Develop targeted strategies to improve these products, whether through marketing initiatives, product enhancements, or re-evaluation of pricing strategies

## Focus on Underperforming Sectors: 
Utilize insights from the tornado chart to develop targeted sales strategies for sectors with lost deals. Conduct a root cause analysis to understand the factors contributing to these losses and implement corrective measures. Consider providing additional training or resources for the sales team in these sectors to enhance their effectiveness.

## Targeted Development for Sales Agents:
Use the sales agent performance table to identify specific training needs for agents who are underperforming. Implement personalized development plans to enhance their skills and increase their contribution to the team’s success.

## Improve Sales Process Efficiency: 
Given the lack of correlation between average closure time and total sales, investigate the sales process for inefficiencies. Implement process improvements, such as training sales representatives on effective closing techniques, adopting sales enablement tools, or streamlining communication between teams. Monitor changes to determine their impact on both closure times and sales figures.

## Customer Engagement and Feedback: 
Increase customer engagement efforts to gather insights on product performance directly from users. Implement surveys or feedback mechanisms to understand their needs and experiences, which can inform product development and sales strategies.

## Promote Healthy Competition: 
Use the team ranking data to encourage a competitive spirit among managers. Consider implementing incentive programs or recognition awards for top-performing teams, which can motivate all teams to strive for higher performance.

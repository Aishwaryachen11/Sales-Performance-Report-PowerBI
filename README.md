## **POWER BI SALES PERFORMANCE DASHBOARD**
### **Introduction:**
In the ever-evolving business landscape, companies are constantly seeking ways to harness data to drive strategic decision-making and improve performance. The ability to monitor key performance indicators (KPIs) and track them over time is crucial for understanding market trends, identifying opportunities, and addressing challenges. This Power BI Sales Performance Dashboard project is designed to fulfill this need by offering a dynamic and interactive platform for analyzing sales data.

This dashboard provides a comprehensive view of a company’s sales performance, allowing users to explore various dimensions such as time, geography, and product categories. By comparing Year-to-Date (YTD) metrics against Prior Year-to-Date (PYTD) metrics, the dashboard helps identify growth patterns, seasonal trends, and areas where performance is lagging. It also supports in-depth analysis by enabling users to drill down into specific data points, filter results based on multiple criteria, and visualize complex data relationships in an easily digestible format.

The Power BI Sales Performance Dashboard is an indispensable tool for sales managers, financial analysts, and business executives who need to quickly and effectively analyze sales data, compare current performance with historical benchmarks, and make informed decisions that align with the company’s strategic goals.

### **Objectives:**

The primary objectives of the Power BI Sales Performance Dashboard are:

**Visualize Sales Performance:**
Provide an intuitive and visually appealing representation of the company’s sales performance across various dimensions such as time, region, and product category.
Compare Current and Past Performance:
Enable users to compare Year-to-Date (YTD) metrics with Prior Year-to-Date (PYTD) metrics to assess growth, identify trends, and highlight areas of concern.

**Drill-Down Capabilities:**
Allow users to drill down into specific data points for a more detailed analysis, enabling them to explore underlying factors that contribute to performance metrics.
Highlight Top and Bottom Performers:
Identify the top and bottom-performing countries, products, or regions based on sales performance and profitability metrics, helping users focus on areas that require attention.

**Interactive Exploration:**
Provide interactive features such as slicers, filters, and dynamic visuals to allow users to customize their view and explore the data from different perspectives.

**Support Decision-Making:**
Serve as a decision-support tool by offering insights into sales trends, profitability, and performance across different segments, helping management make data-driven decisions.

### **Dataset Overview:**
The dataset used for this Power BI dashboard comprises various tables that provide a comprehensive view of sales transactions, account details, product hierarchies, and time dimensions. The dataset includes the following key tables:

**Fact_Sales:**
The Fact_Sales table is the central fact table in this dashboard, containing detailed transactional data for sales. It captures every sale made by the company and includes fields such as Account_id, Date_Time, Price_USD, Product_id, Quantity, COGS_USD, and Sales_USD. This table is used to calculate key metrics like total sales, gross profit, and the cost of goods sold (COGS).

**Dim_Account:**
The Dim_Account table is a dimension table that stores information about the company’s accounts, including their locations and hierarchical relationships. Key fields include Account_id (which links to the Fact_Sales table), Country, Master_id, and other geographical data such as latitude and longitude. This table is crucial for analyzing sales performance across different regions and accounts.

**Dim_Product:**
The Dim_Product table provides a detailed categorization of products sold by the company. It includes fields like Product_Family, Product_Group, Product_Name, and Product_Type. This dimension table allows users to drill down into sales data by product categories and analyze which products or groups are driving sales and profitability.

**Dim_Date:**
The Dim_Date table is a custom date dimension created within Power BI to facilitate time-based analysis. It includes a continuous range of dates and additional calculated fields for various time periods. The Dim_Date table is pivotal for performing time intelligence calculations such as YTD, PYTD, and month-over-month comparisons.

### **Creating the Fact and Dimension Tables**
**Fact_Sales Table:**
Source: The data for the Fact_Sales table typically comes from the company's sales transaction system, such as an ERP (Enterprise Resource Planning) system or CRM (Customer Relationship Management) software.
Fields: The key fields include:
Account_id: Links each sale to a specific account in the Dim_Account table.
Date_Time: Captures the date and time of each sale.
Price_USD: The price at which the product was sold.
Product_id: Links each sale to a specific product in the Dim_Product table.
Quantity: The number of units sold.
COGS_USD: The cost associated with producing the goods sold.
Sales_USD: The total sales amount in USD.

**Dim_Account Table:**
Source: Account information is typically sourced from the company's customer management system, which maintains detailed records of each account, including their location and hierarchical relationships.
Fields: The key fields include:
Account_id: The unique identifier for each account, used to link with the Fact_Sales table.
Country: The country where the account is based, enabling regional analysis.
Master_id: An identifier for parent accounts, which can be used to analyze sales at a group level.
Geographical Data: Fields like latitude, longitude, postal code, and street name for geographic analysis.

**Dim_Product Table:**
Source: Product information is typically sourced from the company's product management system, which maintains detailed records of each product, including its categorization.
Fields: The key fields include:
Product_Family: The high-level category of the product (e.g., Electronics, Clothing).
Product_Group: A sub-category within the product family.
Product_Name: The specific name of the product.
Product_Type: The type of product (e.g., Indoor, Outdoor).

**Dim_Date Table:**
Creation: The Dim_Date table is created within Power BI using DAX (Data Analysis Expressions) to generate a continuous calendar range and additional calculated fields for time intelligence.
Dim_Date:This DAX function generates a table of dates from January 1, 2022, to December 31, 2024. Inpast: This calculated column identifies dates that fall within the same period in the previous year, enabling accurate PYTD calculations.

Dim_Date = 
CALENDAR(
    DATE(2022, 1, 1),
    DATE(2024, 12, 31)
)

Inpast = 
VAR lastsalesdate = MAX(Fact_Sales[Date_Time])
VAR lastsalesdatePY = EDATE(lastsalesdate,-12)
RETURN
Dim_Date[Date]<= lastsalesdatePY

## **Slicers and Filters**
**1. Year Filter:**
Allows users to switch between different years (e.g., 2023, 2024).
Interacts with all visuals to update data based on the selected year.
**2. Metric Slicers:**
Users can switch between metrics like Sales, Gross Profit, and Quantity.
Impacts all measures and titles dynamically across the dashboard.
**3. Product and Region Filters:**
Filters for product categories and regions allow detailed analysis of specific segments.
These filters interact with all visuals, allowing a focused view of the data.

### **Visualizations and Interactions:** 
The dashboard is designed with a variety of visuals, each serving a specific purpose in conveying insights from the sales data. Below are the details of each visualization, including the slicers, filters, and interactions applied.The KPI cards in the dashboard serve as a quick and powerful summary of the company’s most critical sales metrics. For senior management, these cards are the starting point for any data-driven discussion or decision-making process. The KPIs provide an immediate snapshot of the company’s current performance compared to the previous year, highlighting key areas that may require attention.

#### **1. KPI Cards: Key Performance Indicators at a Glance**

<img src="https://github.com/Aishwaryachen11/Sales-Performance-Report-PowerBI/blob/main/Images/KPI%20Cards.png" alt="Description" width="400"/>

**Chart Overview:**
Chart Type: KPI Cards
Title: Key Performance Indicators (YTD, PYTD, YTD vs PYTD Difference, GP%)
Values Displayed:
YTD (Year-to-Date) Sales or Gross Profit
PYTD (Prior Year-to-Date) Sales or Gross Profit
YTD vs PYTD Difference
GP% (Gross Profit Percentage)

**Components:**
YTD (Year-to-Date): This card shows the total sales or gross profit accumulated from the start of the year up to the current date. It’s an essential metric for understanding how well the company is performing in the current fiscal year. Displays the cumulative gross profit or sales from the start of the current year to the present date.
PYTD (Prior Year-to-Date): This KPI provides the equivalent metric for the same period in the previous year. By comparing YTD and PYTD, management can gauge whether the company is growing or falling behind. Shows the equivalent cumulative gross profit or sales for the same period in the previous year.
YTD vs PYTD Difference: This KPI highlights the absolute difference between YTD and PYTD. A positive value indicates growth, while a negative value signals a decline, prompting further investigation. Highlights the absolute difference between the current year’s YTD and last year’s PYTD. Positive values indicate growth, while negative values suggest a decline.
GP% (Gross Profit Percentage): This KPI shows the profitability ratio, calculated as Gross Profit divided by Sales. It’s a crucial indicator of how efficiently the company is managing its costs relative to sales. Represents the ratio of gross profit to sales, indicating the efficiency of the company in generating profit relative to sales.

**Insights from the Chart:**
Performance at a Glance: The KPI cards provide a quick overview of the company’s performance, allowing senior management to instantly assess whether the company is on track to meet its goals.
Immediate Action Points: Significant discrepancies in the YTD vs PYTD Difference can prompt further investigation, enabling management to take timely corrective actions if necessary.
Profitability Monitoring: The GP% card helps track the company's profitability, ensuring that increased sales do not come at the expense of profit margins.
Strategic Decision-Making: These KPIs support data-driven decisions by highlighting areas that need attention, ensuring that management can prioritize actions effectively.

#### **2. Waterfall Chart: Gross Profit YTD vs PYTD | Month - Country - Product**

<img src="https://github.com/Aishwaryachen11/Sales-Performance-Report-PowerBI/blob/main/Images/Waterfall%20Chart.png" alt="Description" width="400"/>

**Chart Overview:**
Chart Type: Waterfall Chart
Title: Gross Profit YTD vs PYTD | Month - Country - Product
Y-Axis: Difference between YTD and PYTD Gross Profit

**Components:**
Green Bars: Indicate an increase in the Gross Profit when comparing the current year's YTD to the previous year's PYTD for a specific month.
Red Bars: Indicate a decrease in the Gross Profit when comparing the current year's YTD to the previous year's PYTD for a specific month.
Blue Bar: Represents the Total difference in Gross Profit between YTD and PYTD for the entire year (cumulative sum of monthly differences).

The Waterfall Chart is a dynamic tool that visualizes the month-over-month changes in gross profit by comparing the current year to the previous year. This chart is particularly valuable for senior management to identify trends, seasonality, and anomalies at a granular level. The visual breakdown by country and product type allows management to see exactly where gains or losses are occurring.
•	Increases and Decreases: The green and red bars immediately signal increases or decreases in gross profit, making it easy to identify periods of concern or celebration.
•	Total Impact: The final blue bar shows the cumulative YTD vs PYTD difference, providing a clear summary of the overall performance across the months.

**Insights from the Chart:**
Month-over-Month Comparison:
The chart allows you to see the performance of Gross Profit month over month. For example, if a bar is green, the current year's Gross Profit for that month is higher than the same month last year. If it is red, it’s lower.
Total Impact:
The blue bar at the end shows the cumulative difference across all months. This gives a quick sense of whether the overall year has been better or worse than the previous year in terms of Gross Profit.
Detailed Breakdown:
The categories (Country, Product_Type, Product_Name) allow for a detailed breakdown of where these differences are coming from. This can help identify specific countries or products that are driving increases or decreases in Gross Profit.
Seasonality:
By looking at the trends across months, you can identify seasonal patterns. For instance, a consistent dip in certain months across both years might indicate a seasonal trend rather than a performance issue.

#### **3. Line and Clustered Column Chart: Gross Profit YTD & PYTD | Month**

<img src="https://github.com/Aishwaryachen11/Sales-Performance-Report-PowerBI/blob/main/Images/Line%20%26%20Clustered%20Column%20Cart.png" alt="Description" width="400"/>

**Chart Overview:**
Chart Type: Line and Clustered Column Chart
Title: Gross Profit YTD & PYTD | Month
Axes:
X-Axis: Time (broken down by Date, Quarter, and Month)
Column Y-Axis: Value YTD (Year-to-Date)
Line Y-Axis: Value PYTD (Prior Year-to-Date)

**Components:**
Columns:
The blue bars in the chart represent the YTD Gross Profit for each month, segmented by Product_Type (Indoor, Landscape, Outdoor).
The height of each bar shows the total Gross Profit for the respective month, segmented by product type.
Red Line:
The red line represents the Value PYTD, which is the Prior Year-to-Date Gross Profit for each month.
The line provides a trend of how the current year's gross profit compares to the same period last year.

The Line and Clustered Column Chart offers a dual perspective on sales performance by showing both the YTD and PYTD gross profit side by side for each month. This chart is instrumental for senior management to compare current performance against historical benchmarks and to visualize how different product types contribute to overall profitability.
•	Side-by-Side Comparison: The columns allow for a clear comparison between YTD and PYTD, highlighting whether the company is improving or falling behind.
•	Trend Identification: The line chart superimposed on the columns helps management identify trends over time, such as whether performance is improving, stable, or declining as the year progresses.

**Insights from the Chart:**
Comparative Analysis:
The chart allows users to compare the current year's Gross Profit with that of the previous year for each month.
By visualizing both YTD (columns) and PYTD (line), it becomes easier to see whether the company is improving or lagging behind compared to last year.
Product Performance:
The color-coded bars provide insight into which product types are contributing the most to gross profit during each month.
This breakdown can help in identifying trends, such as seasonal variations in product performance.
Seasonality and Trends:
If the red line consistently outperforms the columns, it indicates that the current year is doing better than the previous year. Conversely, if the columns are higher, it indicates a positive trend in gross profit growth year-over-year.

#### **4. Scatter Plot: Account Profitability Segmentation | GP% and Gross Profit**

<img src="https://github.com/Aishwaryachen11/Sales-Performance-Report-PowerBI/blob/main/Images/Scatter%20Plot.png" alt="Description" width="400"/>

**Chart Overview:**
Chart Type: Scatter Plot
Title: Account Profitability Segmentation | GP% and Gross Profit
Axes:
X-Axis: Value YTD (Year-to-Date)
Y-Axis: GP% (Gross Profit Percentage)

**Components:**
Data Points (Dots):
Each dot represents an individual account.
The position of the dot on the X-axis represents the YTD value for that account.
The position of the dot on the Y-axis represents the GP% (Gross Profit Percentage) for that account.
Red Dashed Lines:
These lines are used as reference lines to help segment the scatter plot into quadrants.
Vertical Dashed Line: This line is likely positioned at a specific Value YTD threshold, helping to distinguish accounts that contribute more or less to the overall YTD value.
Horizontal Dashed Line: This line is positioned at a specific GP% threshold, helping to distinguish accounts based on their profitability (higher GP% indicates higher profitability).
Purpose: These lines help in visually segmenting the accounts into four quadrants, which can be interpreted as:
Top Right (High YTD Value, High GP%): Most profitable and high-contributing accounts.
Top Left (Low YTD Value, High GP%): Profitable but low-contributing accounts.
Bottom Right (High YTD Value, Low GP%): High-contributing but less profitable accounts.
Bottom Left (Low YTD Value, Low GP%): Least profitable and low-contributing accounts.
•	High GP%, High Gross Profit: Accounts in this quadrant are the company’s most valuable. These are the accounts to nurture and grow.
•	High GP%, Low Gross Profit: These accounts are profitable but contribute less to the overall revenue. Management may explore opportunities to increase sales volume.
•	Low GP%, High Gross Profit: These accounts generate significant revenue but at lower margins. They might require cost optimization or price adjustments.
•	Low GP%, Low Gross Profit: These accounts are underperforming and may need reevaluation.

**Filters and Slicers:**
X-Axis (Value YTD):
This axis represents the total value generated by each account Year-to-Date.
Filter/Slicer Impact: If you adjust the range or selection for this axis, it will filter the accounts based on their YTD contribution. For example, you can focus on high-value accounts by setting a minimum threshold on the X-axis.
Y-Axis (GP%):
This axis represents the gross profit percentage for each account.
Filter/Slicer Impact: Adjusting this will filter accounts based on their profitability. For instance, you can focus only on highly profitable accounts by setting a minimum threshold on the Y-axis.

**Insights from the Chart:**
The Scatter Plot is an advanced analytical tool that segments accounts based on their gross profit and profitability percentage. For senior management, this visual is invaluable for identifying which accounts are most profitable and which may require strategic attention, such as renegotiation of terms or targeted marketing efforts
Profitability vs. Contribution: This chart allows you to visually assess which accounts are both highly profitable (high GP%) and contribute significantly to total sales (high YTD value).
Segmentation: The scatter plot helps in segmenting accounts into different categories, allowing the business to target strategies for different segments (e.g., improving profitability for high-value, low-profit accounts).
Trend Identification: By observing the distribution of accounts, you can identify trends or outliers, such as accounts that are performing exceptionally well or poorly.

#### **5. Multi-Row Card: Top 5 Countries with High YTD Vs PYTD Difference**

<img src="https://github.com/Aishwaryachen11/Sales-Performance-Report-PowerBI/blob/main/Images/Multirow%20Card.png" alt="Description" width="230"/>

**Chart Overview:**
Chart Type: Multi-Row Card
Title: Top 5 Countries with High YTD vs PYTD Difference
Values Displayed:
Country Name
YTD vs PYTD Difference

**Components:**
Country: The name of each country listed, showing where the largest differences between YTD and PYTD are occurring.
YTD vs PYTD Difference: The numerical value representing the difference in sales or gross profit between the current year and the previous year for each country. Negative values indicate a decline, while positive values indicate growth.

**Insights from the Chart:**
Focus on Key Regions: The Multi-Row Card helps management quickly identify which countries are driving the most significant changes in sales performance, enabling them to focus their analysis on these regions.
Identify Opportunities and Risks: Countries with large positive differences may represent growth opportunities, while those with large negative differences may signal risks that need to be managed.
Regional Performance Comparison: This visual allows for easy comparison between the top-performing and underperforming regions, supporting strategic decisions on resource allocation, market focus, and sales strategies.
Actionable Insights: If a top-performing country shows a declining trend, it can prompt a deeper dive into the reasons behind the decline, such as market conditions, competition, or internal challenges.

The Multi-Row Card provides a concise list of the top 5 countries with the largest discrepancies between YTD and PYTD sales performance. This visual is particularly useful for senior management to quickly identify which countries are experiencing the most significant changes—whether positive or negative.
•	Top 5 Rankings: The card shows which countries have the largest differences, helping management focus on the most critical regions.
•	Quick Comparison: The format allows for a quick and easy comparison of performance across different countries.

#### **6. Matrix Visuals: Top 5 Countries by YTD and PYTD**

<img src="https://github.com/Aishwaryachen11/Sales-Performance-Report-PowerBI/blob/main/Images/Matrix%20Visuals.png" alt="Description" width="230"/>

**Chart Overview:**
Chart Type: Matrix Visuals
Title: Top 5 Countries by YTD and PYTD
Rows: Country Name
Columns: YTD and PYTD Gross Profit or Sales

**Components:**
Rows (Country): The list of countries, showing the top 5 based on YTD or PYTD performance. Each country occupies a row in the matrix.
YTD and PYTD Values: The numerical values representing the gross profit or sales for each country for the current year (YTD) and the previous year (PYTD).
Columns: The columns are divided into YTD and PYTD metrics, allowing for side-by-side comparison of the two time periods.

**Insights from the Chart:**
Top Performer Identification: The Matrix Visuals help management identify which countries are performing the best in the current year, as well as those that were top performers in the previous year. This can highlight shifts in market dynamics or changes in competitive positioning.
Year-over-Year Comparison: By comparing YTD and PYTD side by side, management can quickly see if a country’s performance has improved or declined year-over-year, providing insights into trends and patterns.
Focus on Strategic Regions: The Matrix allows management to focus on the top 5 countries that contribute the most to overall sales or gross profit, ensuring that efforts are concentrated where they can have the most impact.
Benchmarking: PYTD values serve as a benchmark, helping management understand how current performance stacks up against last year’s performance and whether the company is on track to meet its goals.

The Matrix Visuals provide a detailed breakdown of the top 5 countries by YTD and PYTD metrics, allowing for an in-depth comparison of current versus prior year performance. For senior management, these visuals are crucial for understanding which countries are leading in sales and which may require strategic adjustments.
•	YTD Performance: Shows the current year’s top performers, highlighting where the company is currently excelling.
•	PYTD Performance: Provides a benchmark by showing last year’s top performers, helping management understand shifts in market dynamics.
Scenario Analysis:
Management can apply filters to focus on specific product categories or regional groupings to see how different areas are performing. Additionally, using time filters, they can assess performance across different quarters or months.

#### **Scenario 1: Yearly Performance Analysis of Outdoor Products (2023)**

<img src="https://github.com/Aishwaryachen11/Sales-Performance-Report-PowerBI/blob/main/Images/Scenario%201.png" alt="Description" width="450"/>

Filters to Apply:
Year: 2023
Product Type: Outdoor Products
Time Period: Full Year (January to December)

**1. Annual Sales Growth:**
Modest Growth in Gross Profit: The Year-to-Date (YTD) gross profit for Outdoor Products in 2023 stands at $1.93M, with a slight increase compared to the Prior Year-to-Date (PYTD) gross profit of $1.85M, resulting in a positive difference of $76.93K. This indicates modest growth in gross profit for the Outdoor Products category over the previous year.
Key Markets: From the Multi-Row Card, it is evident that countries like China, Sweden, and Brazil have been significant contributors to gross profit, with China leading the charge. However, despite the overall positive trend, some countries like Sweden have experienced a notable negative difference in YTD vs PYTD, suggesting challenges in certain markets.

**2. Seasonal Peaks:**
Summer Surge in Sales: The Waterfall Chart and the Line and Clustered Column Chart both indicate a significant increase in gross profit during the summer months, particularly in June ($58K) and July ($77K). This surge aligns with the seasonal nature of Outdoor Products, where demand typically spikes during warmer months as consumers engage in more outdoor activities.
Effective Summer Campaigns: The spike in sales during June and July could also be attributed to successful marketing campaigns or promotional efforts targeted at boosting sales of Outdoor Products during the peak season. This highlights the effectiveness of timing campaigns to coincide with periods of high consumer demand.

**3. Profitability Trends:**
Stable Profit Margins: The GP% (Gross Profit Percentage) for Outdoor Products has remained strong at 40.10%, reflecting stable profitability despite the fluctuations in gross profit throughout the year. This suggests that the company has effectively managed its costs and pricing strategies, maintaining healthy profit margins even as sales volumes vary.
Market-Specific Challenges: While the overall profitability is stable, the Multi-Row Card highlights that certain markets, such as Sweden and Thailand, have experienced a decline in YTD vs PYTD gross profit, which may be affecting the overall profitability in those regions. It may be necessary to investigate the reasons behind these declines, such as increased competition, pricing pressures, or changing consumer preferences.

**Recommendations:**
Focus on High-Performing Markets: Given the strong performance in countries like China and Brazil, consider focusing marketing efforts and resources on these regions to further capitalize on the growth. These markets show a strong positive difference in YTD vs PYTD, indicating potential for continued expansion.
Address Market-Specific Challenges: Investigate the factors contributing to the decline in gross profit in countries like Sweden and Thailand. This could involve reviewing pricing strategies, evaluating the competitive landscape, or adjusting the product mix to better align with local consumer preferences.
Leverage Seasonal Trends: Continue to leverage the seasonal demand for Outdoor Products by planning targeted marketing campaigns around the summer months. The sales surge during June and July suggests that consumers are highly responsive to promotions during this period, making it an ideal time for new product launches or discounts.

#### **Scenario: Sales Performance Analysis in China for 2023**

<img src="https://github.com/Aishwaryachen11/Sales-Performance-Report-PowerBI/blob/main/Images/Scenario%202.png" alt="Description" width="450"/>

**1. Market Share and Growth**
YTD vs PYTD Analysis:
Significant Decline in Gross Profit: The Year-to-Date (YTD) gross profit for China in 2023 is $1.53M, which is considerably lower than the Prior Year-to-Date (PYTD) gross profit of $1.93M. This results in a negative difference of -$405K, indicating a substantial decline in gross profit compared to the previous year.
Negative Market Growth: The significant drop in gross profit suggests that the company is losing market share in China, which could be due to increased competition, a slowdown in demand, or challenges within the company's operations in this market.

**2. Product Preferences**
Product Type Performance:
Outdoor Products Underperformance: The Line and Clustered Column Chart shows that while there was some consistency in sales volume across different product types, the overall performance of Outdoor Products in China has been weak in 2023. The demand did not pick up as strongly as in previous years, leading to underperformance.
Limited Impact of Promotional Efforts: Despite any efforts to promote Outdoor Products, the sales in this category have not shown significant improvement, as reflected in the stagnant or declining gross profit margins throughout the year.

**3. Seasonal Trends**
Monthly/Quarterly Breakdown:
Gradual Decline Across the Year: The Waterfall Chart indicates that the gross profit in China experienced a consistent decline each month, particularly noticeable in the second half of the year. Significant drops occurred in February (-$58K), March (-$6K), and continued declines in June and September.
Lack of Seasonal Uplift: Typically, one might expect a seasonal uplift in sales during certain months; however, the data suggests that any seasonal demand that might have been anticipated did not materialize in 2023, contributing to the overall poor performance.

**4. Profitability**
GP% Analysis:
Declining Profit Margins: The Gross Profit Percentage (GP%) for China is recorded at 37.87%, which is lower than what might have been expected, given the overall gross profit levels. This decrease in GP% indicates that while sales might be occurring, they are potentially being driven by lower-margin products, increased discounting, or higher costs, which are eroding profitability.
Profitability Concerns: The declining GP% combined with the negative YTD vs PYTD difference suggests that not only is the market shrinking in terms of revenue, but it is also becoming less profitable, which raises concerns about the sustainability of operations in this region.

**Recommendations:**
Strategic Review of Market Positioning:
Conduct a thorough analysis of the competitive landscape in China to understand the factors contributing to the decline in market share and gross profit. This might include investigating competitors' pricing strategies, product offerings, or marketing tactics.
Targeted Product Strategy:
Consider re-evaluating the product mix offered in China, focusing on higher-margin products or those with greater demand potential. Additionally, explore opportunities to introduce new product lines or variants that could better align with local consumer preferences.
Revamp Marketing and Sales Efforts:
Given the lack of seasonal uplift and the overall decline in sales, it may be necessary to overhaul the marketing strategy for China. 

________________________________________
### **Conclusion**
This Power BI Sales Performance Dashboard project offers a powerful, interactive tool for senior management to analyze sales data across key metrics such as Year-to-Date (YTD) and Prior Year-to-Date (PYTD) comparisons, gross profit margins, and regional performance. By utilizing dynamic visualizations and filters, the dashboard provides actionable insights into market trends, product performance, and profitability, enabling data-driven decisions that drive business growth. Through this project, we demonstrate the value of transforming raw data into strategic intelligence, ultimately supporting the company's objectives of optimizing sales and expanding market share.



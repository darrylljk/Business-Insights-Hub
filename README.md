# Adventure Works Business Insights Hub
## Adventure Works
AW is a fictional company, created by Microsoft, that manufactures and sells bicycles, bicycle parts, and accessories along with other related products.

For this project, I am using the `AdventureWorks Sales` dataset.

Link: [Adventure Works Sales Data](https://github.com/microsoft/powerbi-desktop-samples/blob/main/AdventureWorks%20Sales%20Sample/AdventureWorks%20Sales.xlsx)

## Project Overview - Business Insights Hub
I've developed the Business Insights Hub (BIH) as a comprehensive analytics & insights platform for Adventure Works (AW), offering insights into various facets of the business using AW's sales data. This platform serves as a one-stop shop for understanding key areas, including sales performance, customer segments, product trends, purchasing patterns, and reseller performance.

Key highlights include demand forecasting, RFM customer segmentation analysis, executive sales report, sales and profitability by region, product trends, seasonal patterns, and reseller performance evaluation.

This platform provides AW with actionable insights to drive strategic decision-making and business growth.

## Product Gallery
[Gallery PDF Link](%5BPDF%5D%20-%20AW%20BIH.pdf)

![Home Page](https://github.com/user-attachments/assets/d2184ea7-3574-4f06-ad62-788101474563)
![Sales Report](https://github.com/user-attachments/assets/7abcd055-12de-4a1a-bce7-ee0f38fdb800)
![Customer Insights](https://github.com/user-attachments/assets/c2f0163d-4389-4e5e-84ea-97b0361d2386)
![Orders Analysis](https://github.com/user-attachments/assets/7a8bc339-d18f-4007-ae87-b3742b0bbbd8)
![Resellers Performance](https://github.com/user-attachments/assets/752bf521-7161-40c6-98e8-1db1566d5139)
![Products & Demand Forecasting](https://github.com/user-attachments/assets/40bce79c-7891-4242-9f10-4e3dcf7c2f39)
![Sales Data Download](https://github.com/user-attachments/assets/eb478ce8-76ef-4d68-af0b-d496a4ea48f2)

## Analysis and Insights
#### Overview
- both sales and profit have shown a consistent upward trend from 2019 to 2020
- key markets: US and Australia accounts for most sales and profits
- bikes are the primary revenue driver, contributing significantly to overall financial performance
- most units sold are accessories
- average order value = $720, with a positive profit margin (indicating healthy financial situation)
- profit represents approx. 2/5 of total sales, reflecting strong profitability
- secured 18K customers in FY20, 10% being new customers, however, 5% of customers are lost during the year

#### Customers
- champion and loyal customers account for approx. 15% of customer base, implement reward and membership system to engage and retain these high-value customers
- 10% of customers are potential loyalists, nurture them through personalized offers
- 10% of customers are new, focus on onboarding and engagement strategies, convert them to long-term customers
- around 30% of customers are at risk -> win them back with renewals, discount, new products that cater to their needs
- dormant customers, about to "sleep" -> recommend popular products or those likely to appeal to their preferences
- gain deeper understanding of customer base, proportion of hobbyists, large families, and othe rkey segments.
- export individual segments for targeted marketing and strategic support
- add CLV and churn prediction to monitor customer status

#### Orders
- most orders were placed between march and may, indicating seasonal surge in demand, adjust inventory accordingly
- timing: orders were usually placed in the middle of the week, suggesting customers prefer to make purchases during weekdays, likely in anticipation of the weekend
- US and Aus accounts for most orders, most important markets
- tires and tubes, bottles and cages, helmets are the most frequently ordered product categories
- noticeable upward trend of high AOV order, indicating increase in premium or bulk purchases over time
- introduce premium product bundles / volume-based discounts to encourage higher AOV purchases across various product categories
- focus marketing effort on top-selling categories with cross-selling opportunities for related accessories and upgrade

#### Reseller
- most sales were made to warehouse and value-added resellers
- total of $36M sales were made to resellers in FY20
- not all sales to resellers generated a profit, suggesting the need to evaluate the terms and profitability of reseller agreements
- assess profitability of each reseller to identify high- and low-performing partners
- focus on strengthening relationships with high margin resellers
- revisit pricing / contract structures with those that consistently underperform / return loss
- diversify reseller base to expand into other reseller segments ot regions to increase sales
  
#### Product
- best selling SKUs (sales amount) are the mountain bike mountain-200 series and road-250 series
- focus on promoting popular products, expand inventory, and offer bundled deals to capitalize on their popularity
- conduct basket analysis and association rule mining to discover frequent itemsets
- product bundling, cross selling, and store layout optimization (arrange frequently bought-together items together in physical stores and on e-commerce sites to increase convenience and sales)

#### Future Work / Other Ideas & Improvements
- customer life time value analysis
- churn prediction
- anomaly detection (unusual sales spikes / dips)
- product recommendation system
- basket analysis and association rule mining
- competitor analysis
- demographic segmentation
- what-if scenario planning
- data quality monitoring

## Building the platform on Power BI
### Understanding the data - data Dictionary
This data set contains 7 tables, which we'll categorize into (F) Fact and (D) Dimension tables.

#### Fact Tables
##### 1. Sales: contains sales transaction details

| Column Name | Description |
| --- | --- |
| SalesOrderLineKey | A unique identifier for each line item in a sales order. |
| ResellerKey | Identifier for the reseller who processed the sale. |
| CustomerKey | Identifier for the customer who placed the order. |
| ProductKey | Identifier for the product sold. |
| OrderDateKey | Date when the order was placed, represented in a date dimension format (e.g., YYYYMMDD). |
| DueDateKey | The due date for the order, represented in a date dimension format (e.g., YYYYMMDD). |
| ShipDateKey | The date when the product was shipped, represented in a date dimension format (e.g., YYYYMMDD). |
| SalesTerritoryKey | Identifier for the sales territory that the order was associated with. |
| Order Quantity | The number of units of the product ordered. |
| Unit Price | The price of a single unit of the product before any discounts. |
| Extended Amount | The total price for the ordered quantity of the product (Unit Price * Order Quantity). |
| Unit Price Discount Pct | The percentage discount applied to the unit price. |
| Product Standard Cost | The standard cost of the product before any adjustments or discounts. |
| Total Product Cost | The total cost of the ordered quantity of the product (Product Standard Cost * Order Quantity). |
| Sales Amount | The total sales amount for the line item, after discounts are applied (Extended Amount - Discount). |

##### 2. Sales Order: track individual sales order lines 
| Column Name | Description |
| --- | --- |
| Channel | The sales channel for the order (e.g., "Reseller") |
| SalesOrderLineKey | Unique identifier for the sales order line |
| Sales Order | Unique identifier for the sales order |
| Sales Order Line | Unique identifier for the specific sales order line (combination of Sales Order and line number) |

#### Dimension Tables
##### 1. Product: product lookup
| Column Name | Description |
| --- | --- |
| ProductKey | Unique identifier for each product. |
| SKU | Stock Keeping Unit, a unique identifier used for inventory management. |
| Product | Name and description of the product, including size or color where applicable. |
| Standard Cost | The standard cost to produce or acquire the product. |
| Color | The color of the product. |
| List Price | The selling price of the product. |
| Model | Model name or series to which the product belongs. |

##### 2. Customer: customer lookup
| Column Name | Description |
| --- | --- |
| CustomerKey | Unique identifier for each customer. |
| Customer ID | Alphanumeric identifier specific to each customer. |
| Customer | Full name of the customer. |
| City | City where the customer resides. |
| State-Province | State or province of the customer’s location. |
| Country-Region | Country or region of the customer. |
| Postal Code | Postal or ZIP code for the customer’s address |

##### 3. Reseller: reseller lookup
| Column Name | Description |
| --- | --- |
| ResellerKey | Unique identifier for each reseller |
| Reseller ID | A unique code representing the reseller |
| Business Type | Type of business or organization the reseller represents |
| Reseller | Name of the reseller or business |
| City | City where the reseller is located |
| State-Province | State or province where the reseller is located |
| Country-Region | Country or region where the reseller is located |

##### 4. Sales territory: sales territory lookup
| Column Name | Description |
| --- | --- |
| SalesTerritoryKey | Unique identifier for each sales territory |
| Region | Name of region within sales territory |
| Country | Country associated with sales territory |
| Group | Grouping of territory based on organizational divisions |

##### 5. Date: date lookup
| Column Name | Description |
| --- | --- |
| DateKey | Unique identifier for each date in YYYYMMDD format. |
| Date | The actual date in MM/DD/YYYY format. |
| Fiscal Year | The fiscal year associated with the date (e.g., FY2018). |
| Fiscal Quarter | The fiscal quarter associated with the date (e.g., FY2018 Q1). |
| Month | The month and year of the date in "YYYY MMM" format, indicating the month within a specific year (e.g., 2017 Jul). |
| Full Date | The complete date in "YYYY MMM, DD" format, providing a full textual representation of the date (e.g., 2017 Jul, 01). |
| MonthKey | Unique identifier for each month in YYYYMM format, used to represent the month without specific day detail (e.g., 201707). |

## Data Ingestion
Data is imported into Power BI through Power Query, where it is cleaned, transformed, and prepared for analysis.

## Data Processing
- appended "F" and "D" to table names to label as fact / dimension for easy reading and access
- applied first rows as headers
- scaled down scope to FY19 & FY20
- handled missing and duplicate values
- ensured consistency in data types
- inspected data quality and data distributions
- checked for outliers
- checked cardinality
- created measures and calculated columns for advanced analysis by writing DAX code
- appended "_" to measures and calculated columns to push to top for easy reading and access
- connected tables using star schema, dimension tables connected to fact tables in a one-to-many relationship
- entity-relationship diagram
- ![image](https://github.com/user-attachments/assets/1d7a383e-4c18-41ee-97b5-6613b4228cbe)

## Contact
Darryl Lee - [LinkedIn](https://www.linkedin.com/in/darryl-lee-jk/)

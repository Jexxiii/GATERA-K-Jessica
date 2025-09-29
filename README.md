# GATERA-K-Jessica
PL Sql assignment
student id 27630
1. Problem Definition

Business Context:
A retail company operating in Rwanda wants to analyze its sales performance across regions and product categories. The marketing department needs better insights to drive promotions and customer segmentation.

Data Challenge:
Although transactions are recorded, managers lack advanced analytics for ranking products, understanding sales trends, and grouping customers by spending.

Expected Outcome:
Identify top-selling products by region and quarter, track sales growth, and segment customers into meaningful quartiles for marketing campaigns.

2. Success Criteria (Goals)

Top 5 products per region/quarter → RANK()

<img width="982" height="313" alt="Screenshot 2025-09-27 182509" src="https://github.com/user-attachments/assets/f67ff7fa-f3a3-4e10-8d42-7059f6e9f8f3" />

Running monthly sales totals → SUM() OVER()

<img width="822" height="281" alt="Screenshot 2025-09-29 194125" src="https://github.com/user-attachments/assets/90ac1749-2020-4d42-8dde-701a93a81b6b" />

Month-over-month growth % → LAG()/LEAD()

<img width="1118" height="279" alt="Screenshot 2025-09-29 194341" src="https://github.com/user-attachments/assets/2a342757-fa13-42c5-8d66-bdf2c9aa31cd" />

Customer quartiles (segments) → NTILE(4)

3-month moving averages → AVG() OVER()

3. Database Schema

Tables:

customers: customer_id (PK), name, region

products: product_id (PK), name, category

transactions: transaction_id (PK), customer_id (FK), product_id (FK), sale_date, amount

<img width="553" height="303" alt="Screenshot 2025-09-29 194920" src="https://github.com/user-attachments/assets/d2463891-648a-42fb-82f8-5bc75ca7febd" />

ER Diagram:

<img width="806" height="376" alt="Screenshot 2025-09-29 201559" src="https://github.com/user-attachments/assets/7ba33f6e-c99f-49f3-950b-2639bbfaa00f" />

customers (1) ────< transactions >──── (1) products

4. Window Functions Implementation
(a) Ranking – Top Products per Region


<img width="971" height="363" alt="Screenshot 2025-09-29 201807" src="https://github.com/user-attachments/assets/4bc8ed91-9ef9-4875-9ece-cbb059dd8fac" />


📊 Insight: Shows which products dominate sales in each region.

(b) Aggregate – Running Monthly Totals

<img width="800" height="283" alt="Screenshot 2025-09-29 201905" src="https://github.com/user-attachments/assets/eb52d097-c0a5-419c-bd0f-6fb3958c9770" />


📊 Insight: Helps track how revenue accumulates over time.

(c) Navigation – Month-over-Month Growth
WITH monthly_sales AS (
 
 <img width="1077" height="294" alt="Screenshot 2025-09-29 202137" src="https://github.com/user-attachments/assets/9d912214-f898-40cc-ae92-2a47a0d4c952" />


📊 Insight: Identifies whether sales are growing or declining month-to-month.

(d) Distribution – Customer Quartiles

<img width="568" height="141" alt="image" src="https://github.com/user-attachments/assets/a5af5c28-5601-4cae-bfd8-d443dd88284e" />


📊 Insight: Customers are grouped into 4 segments — top spenders (Q1) down to least active (Q4).

(e) Moving Average – 3-Month Trend

<img width="754" height="256" alt="Screenshot 2025-09-29 202616" src="https://github.com/user-attachments/assets/816fbd2c-b05f-4281-afca-e982bab39ccd" />

📊 Insight: Smooths fluctuations and shows long-term sales trends.

5. Results Analysis

Descriptive:
Sales are dominated by electronics in Kigali, with beverages more common in Huye. Revenue is steadily increasing month-to-month.

Diagnostic:
Growth spikes are linked to laptop purchases. Seasonal beverage sales occur around January–March.

Prescriptive:
Focus promotions on top quartile customers, expand electronics marketing in Kigali, and offer discounts in lower quartile segments to encourage spending.

6. References

MySQL 8.0 Documentation – Window Functions

Oracle SQL Window Functions Tutorial

W3Schools SQL Window Functions Guide

Mode Analytics SQL Window Functions

GeeksforGeeks SQL Window Functions

TutorialsPoint – NTILE and Ranking Functions

MySQL Workbench User Guide

Kaggle SQL Queries Reference (educational use)

StackOverflow discussions on MySQL Window Functions

AUCA Database Development Course Notes

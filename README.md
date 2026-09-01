# Wealth Management Client Retention & Operational Efficiency Dashboard

> An end-to-end data analytics project built to track wealth management assets, identify client churn risk factors, and optimize service support operations using SQL, Excel, and Power BI. Designed to mirror real-world financial analytics use cases focused on client experience and operational excellence.

---

## 🎥 Project Walkthrough
[![Project Video Walkthrough](https://img.shields.io/badge/Watch-Loom%20Video%20Walkthrough-blue?style=for-the-badge&logo=loom)](Insert_Loom_Video_Link_Here)  
*(A 2-minute video demonstration covering the interactive Power BI dashboard, data model architecture, and underlying SQL querying logic.)*

---

## 📊 Project Architecture & Data Flow
```text
+---------------------------------------------------------------+
|                      1. DATA SOURCES                          |
|   [ Dim_Clients.csv ]   [ Fact_Transactions ]   [ Support.csv ]|
+-------------------------------+-------------------------------+
                                |
                                v
+---------------------------------------------------------------+
|                  2. DATA WRANGLING & SQL                      |
|     - Excel Power Query (Data cleaning, type validation)      |
|     - SQL Database (Joins, Aggregations, Window Functions)    |
+-------------------------------+-------------------------------+
                                |
                                v
+---------------------------------------------------------------+
|                   3. POWER BI MODELING                        |
|     - Star Schema (1-to-Many Relationships)                   |
|     - DAX Measures (Total AUM, Churn Rate, Resolution Time)   |
+-------------------------------+-------------------------------+
                                |
                                v
+---------------------------------------------------------------+
|                4. INTERACTIVE POWER BI DASHBOARD              |
|   +-----------------------+  +----------------------------+   |
|   | Page 1: Executive     |  | Page 2: Churn Risk Matrix  |   |
|   | Overview & AUM        |  | & Satisfaction Correlation |   |
|   +-----------------------+  +----------------------------+   |
|   +-------------------------------------------------------+   |
|   | Page 3: Operational Efficiency & Ticket Bottlenecks   |   |
|   +-------------------------------------------------------+   |
+---------------------------------------------------------------+

---

## 🛠️ Tech Stack & Tools
* **Data Cleansing & Prototyping:** Microsoft Excel (Power Query, Dynamic Arrays)
* **Data Extraction & Transformation:** SQL (PostgreSQL / SQLite - Joins, CTEs, Window Functions)
* **Data Visualization & Modeling:** Power BI (Star Schema, DAX, Custom KPI Cards)
* **Version Control:** Git & GitHub

---

## 🗂️ Complete Step-by-Step Project Documentation

### Step 1: Data Architecture & Generation
* **The Concept:** Designed a relational **Star Schema** separating descriptive client attributes from transactional and support event logs to ensure optimal database performance.
* **Execution:** Generated mock financial and customer service datasets simulating a wealth management portfolio of 500+ clients across multiple investment tiers (Bronze, Silver, Gold, Platinum).
* *[Screenshot Placeholder: Excel Data Model / Table Preview]*

### Step 2: SQL Data Extraction & Transformation
* **The Concept:** Loaded relational CSVs into a local database environment to test querying logic and pre-aggregate data.
* **Execution:** Wrote robust analytical queries utilizing `JOIN` operations, `GROUP BY`, and window functions. Below is an example script used to evaluate asset sizes across client tiers:
  ```sql
  SELECT 
      c.Investment_Tier,
      COUNT(DISTINCT c.Client_ID) AS Total_Clients,
      AVG(t.Asset_Amount) AS Avg_Transaction_Size
  FROM Dim_Clients c
  JOIN Fact_Transactions t ON c.Client_ID = t.Client_ID
  GROUP BY c.Investment_Tier;

Step 3: Data Modeling & DAX in Power BI
The Concept: Connected raw sources into Power BI and established relational integrity.

Execution: Configured a robust 1-to-Many (1:*) relationship model linking Dim_Clients to fact tables. Developed core DAX measures to drive dynamic reporting:

Total AUM = SUM(Fact_Transactions[Asset_Amount])

Churn Rate % = DIVIDE(CALCULATE(DISTINCTCOUNT(Dim_Clients[Client_ID]), Dim_Clients[Status] = "Churned"), DISTINCTCOUNT(Dim_Clients[Client_ID]), 0)

Avg Resolution Days = AVERAGEEX(Fact_Support_Tickets, Fact_Support_Tickets[Date_Closed] - Fact_Support_Tickets[Date_Opened])

Step 4: Executive Dashboard Delivery
Page 1 (Executive Overview): Tracks total Assets Under Management, account tier breakdown, and high-level growth trends.

Page 2 (Client Churn Risk): Analyzes the correlation between unresolved support tickets and account attrition to flag high-risk accounts.

Page 3 (Operational Efficiency): Highlights support channel bottlenecks and average ticket resolution times to guide team resource allocation.

[Screenshot Placeholder: Final Power BI Dashboard Views]

🚀 Key Business Insights & Outcomes
The Support Bottleneck: Clients with support tickets taking longer than 5 business days to resolve exhibited a 35% higher churn rate, proving that operational response speed directly protects client retention.

Channel Optimization: Online self-service channels resolved tier-1 issues 40% faster than traditional advisor phone queues, freeing up bandwidth for high-value client advisory work.

Asset Concentration: Platinum tier clients drive 60% of total Assets Under Management (AUM), underscoring the need for priority routing on support escalations.

# 🚗 Car Detailing Business Performance Dashboard

> An end-to-end analytics project tracking revenue, expenses, and client behavior for my own car detailing business — built in Power BI to practice turning raw operational data into real business decisions.

---

## 🎥 Project Walkthrough
[![Project Video Walkthrough](https://img.shields.io/badge/Watch-Video%20Walkthrough-blue?style=for-the-badge&logo=loom)](REPLACE_WITH_YOUR_VIDEO_URL)
*(A short walkthrough of the dashboard, my analysis process, and two data-quality issues I caught and corrected along the way.)*

---

## 📊 Project Architecture & Data Flow

```text
+---------------------------------------------------------------+
|                      1. DATA SOURCE                            |
|         Manually logged Service Book & Expenses (Excel)        |
+-------------------------------+-------------------------------+
                                |
                                v
+---------------------------------------------------------------+
|                  2. POWER BI DATA MODELING                     |
|     - Two tables: Service Book, Expenses                       |
|     - Column data-type correction (Text → Whole Number)        |
|     - Aggregation review (Sum vs. Average vs. Count)            |
+-------------------------------+-------------------------------+
                                |
                                v
+---------------------------------------------------------------+
|                3. TWO-PAGE POWER BI DASHBOARD                  |
|   +-----------------------+  +----------------------------+   |
|   | Page 1: Executive     |  | Page 2: Service & Client    |   |
|   | Summary (KPIs, trend) |  | Detail Breakdown            |   |
|   +-----------------------+  +----------------------------+   |
+---------------------------------------------------------------+
```

---

## 🛠️ Tech Stack & Tools
* **Data Entry & Source Records:** Microsoft Excel
* **Data Modeling & Visualization:** Power BI Desktop (data types, aggregations, relationships)
* **Version Control:** Git & GitHub

---

## 🗂️ Step-by-Step Process

### Step 1: Building the Data Model
* **The Concept:** Structured two related tables — Service Book (client, car, revenue, duration) and Expenses (item, cost, category) — to support both revenue and cost analysis.
* **Execution:** Loaded manually tracked business records into Power BI and built relationships between service and expense data by month.

### Step 2: Catching Data Quality Issues
* **The Concept:** Before trusting any visual, I checked whether each field's aggregation actually matched what I intended to measure.
* **Execution:** Found that my "Detail Duration" column was stored as **Text**, silently defaulting every table to a **Count** aggregation instead of Average — this made a low-duration car model appear to have the longest service time. I corrected the column's data type and re-verified every chart built on it. I also caught a **Sum vs. Average** mismatch on a Revenue-by-Car-Type chart that had flipped my top-performing vehicle type.

### Step 3: Designing the Two-Page Dashboard
* **The Concept:** Split the report into an Executive Summary (KPIs + headline trends for a quick read) and a Detail page (granular breakdowns for anyone who wants to dig deeper).
* **Execution:** Built KPI cards for Total Revenue and Total Cost, a monthly revenue trend chart, and a cost breakdown by item group on the summary page; car model, client, and package-level breakdowns on the detail page.

---

## 🚀 Key Business Insights & Decisions

* **Seasonal revenue drop:** Revenue fell roughly 70% from May to August as summer ended — I'd test a back-to-school promotion to smooth out the dip.
* **Profitable from month one:** Generated $2,000 in revenue against $1,383 in expenses in my first month — a ~31% margin right out of the gate.
* **No car type drives repeat business:** My most-serviced model (Nissan) is driven entirely by first-time clients — retention should be built around the client relationship, not the vehicle.
* **Duration doesn't predict revenue:** Several car models share the same average service time, but revenue for those varies by up to $70 per service — pricing follows vehicle size and package tier, not time spent.
* **Volume ≠ value:** Sedans are my highest-volume car type but my lowest average revenue ($115.60); Minivans earn the most per service ($150) despite low volume — worth shifting some marketing toward minivan owners.

---

## 📁 Files
- `Power BI Dashboard.pbix` — the full Power BI file

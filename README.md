# 🚗 Car Detailing Business Performance Dashboard

> An end-to-end analytics project tracking revenue, expenses, and client behavior for my own car detailing business — built in Power BI to practice turning raw operational data into real business decisions.

---

## 🎥 Project Walkthrough
[![Project Video Walkthrough](https://img.shields.io/badge/Watch-Video%20Walkthrough-blue?style=for-the-badge&logo=loom)](REPLACE_WITH_YOUR_VIDEO_URL)
*(A short walkthrough of the dashboard, my analysis process, and the data-quality issues I caught and corrected along the way.)*

---

## 📊 Project Architecture & Data Flow

```text
+---------------------------------------------------------------+
|                      1. DATA SOURCE                            |
|   Monthly Excel files: Service Book (May-Aug), Expenses (May-June) |
+-------------------------------+-------------------------------+
                                |
                                v
+---------------------------------------------------------------+
|                  2. EXCEL / POWER QUERY CLEANUP                |
|     - Combined monthly files into one table (per category)     |
|     - Fixed column-name mismatch causing null values           |
+-------------------------------+-------------------------------+
                                |
                                v
+---------------------------------------------------------------+
|                  3. POWER BI DATA MODELING                     |
|     - Two tables: Service Book, Expenses                       |
|     - Column data-type correction (Text → Whole Number)        |
|     - Aggregation review (Sum vs. Average vs. Count)            |
+-------------------------------+-------------------------------+
                                |
                                v
+---------------------------------------------------------------+
|                4. TWO-PAGE POWER BI DASHBOARD                  |
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

## 🧹 Excel Data Preparation

Raw service and expense records were tracked in separate monthly Excel files (`2026_05_Service_Book.xlsx` through `2026_08_Service_Book.xlsx`, plus monthly Expenses files) before being combined into a single working dataset (`Dashboard_Data.xlsx`).

**Issues found and fixed while combining the files:**
- **Column name mismatch:** One monthly file had a column labeled differently than the others (`Car` vs. `Car / Service`), which caused that entire month's Service Book data to return null values when merged. Renamed columns to match before combining.
- **Null value troubleshooting:** Traced the null values back to the column mismatch above rather than a data entry issue, and verified all four months merged correctly afterward.
- **Combined all Service Book files into one table and all Expenses files into one table**, rather than transforming everything in a single query — merging both categories at once caused errors, so I processed Service Book and Expenses as two separate transformations.

**Known limitation (not yet cleaned):** Some car entries retain inconsistent formatting from manual data entry (extra trailing spaces, and one recurring misspelling of "Mercedes" as "Mercedez"). These don't affect the aggregate numbers shown on the dashboard, but would be a next step for a cleaner production dataset.

📄 Example raw file: [2026_08_Service_Book.xlsx](2026_08_Service_Book.xlsx)
📄 Combined working file: [Dashboard_Data.xlsx](Dashboard_Data.xlsx)

## 🔄 Power Query Transformations

Within Power BI's Power Query Editor (Transform Data), I:
- Used "Combine Files from Folder" to append the four monthly Service Book files into a single table, and separately for the two monthly Expenses files — each row is tagged with a `Source.Name` column showing which monthly file it came from.
- Diagnosed and resolved the column-mismatch null issue described above before finalizing the merge.
- Processed Service Book and Expenses as two independent query transformations after combining them together caused errors.

---

## 🗂️ Step-by-Step Process

### Step 1: Building the Data Model
* **The Concept:** Structured two related tables — Service Book (client, car, revenue, duration) and Expenses (item, cost, category) — to support both revenue and cost analysis.
* **Execution:** Loaded the combined monthly records into Power BI and built relationships between service and expense data by month.

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
- [Power_BI_Dashboard.pbix](Power_BI_Dashboard.pbix) — the full Power BI file
- [Dashboard_Data.xlsx](Dashboard_Data.xlsx) — combined working dataset (post Power Query merge)
- [2026_08_Service_Book.xlsx](2026_08_Service_Book.xlsx) — example raw monthly source file

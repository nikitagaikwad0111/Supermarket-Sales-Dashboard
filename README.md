# 🛒 Supermarket Sales Dashboard — Looker Studio

> An interactive, multi-page business intelligence dashboard built on a real supermarket transaction dataset to analyze revenue trends, product performance, customer behavior, and payment patterns across 3 branches in Myanmar.

---

## 📌 Project Overview

This is a **3-page Looker Studio dashboard** that transforms raw supermarket sales data into actionable business insights. It simulates a real-world BI reporting workflow — from raw CSV ingestion to an interactive dashboard with filters, scorecards, and cross-page navigation.

| Detail | Info |
|---|---|
| Tool | Google Looker Studio (free tier) |
| Dataset | Supermarket Sales Dataset (CSV) |
| Records | 1,000 transactions |
| Period | January 1, 2019 – March 9, 2019 (Q1 2019) |
| Project type | Data Analytics / Business Intelligence |
| Status | ✅ Complete |

---

## 📊 Dashboard Pages

### Page 1 — Executive Sales Overview
*Monitor overall sales performance, revenue trends, branch performance, and key business KPIs.*

**Scorecards (KPIs):**

| KPI | Value |
|---|---|
| Total Gross Income | 15,379 |
| Total Revenue | 322,967 |
| Total Transactions | 1,000 |
| Total Quantity Sold | 5,510 |

**Charts:**
- Revenue by Product Line (horizontal bar)
- Revenue by Branch (horizontal bar)
- Revenue Trend Over Time (time-series line chart — Jan to Mar 2019)

---

### Page 2 — Product & Operations Analysis
*Analyze product performance, sales volume, operational efficiency, and branch-level performance.*

**Scorecards:**

| KPI | Value |
|---|---|
| Avg Customer Rating | 6.97 |
| Branch C Revenue | 110,569 |
| Top Product Line Revenue | 56,145 |

**Charts:**
- Quantity Sold by Product Line
- Gross Income by Product Line
- Avg Customer Rating by Branch (A: 7.03, B: 6.82, C: 7.07)
- Revenue Contribution by Product Line Across Branches (stacked bar)

---

### Page 3 — Customer & Payment Analysis
*Analyze customer segments, payment preferences, and satisfaction.*

**Charts:**
- Revenue by Payment Method (donut chart)
- Revenue by Customer Type — Member vs Normal
- Average Customer Rating by Product Line
- Revenue by City (Naypyitaw, Yangon, Mandalay)

---

## 🗂️ Dataset Details

**File:** `supermarket_Sales.csv`  
**Rows:** 1,000 | **Columns:** 17 | **Missing values:** None

| Column | Type | Description |
|---|---|---|
| Invoice ID | String | Unique transaction identifier |
| Branch | String | Store branch — A (Yangon), B (Mandalay), C (Naypyitaw) |
| City | String | City of the branch |
| Customer type | String | Member or Normal |
| Gender | String | Female (501) or Male (499) |
| Product line | String | 6 product categories (see below) |
| Unit price | Float | Price per unit (range: 10.08 – 99.96) |
| Quantity | Integer | Units sold per transaction (range: 1 – 10) |
| Tax 5% | Float | 5% tax applied on cost of goods |
| Total | Float | Total transaction value including tax |
| Date | String* | Transaction date in M/D/YYYY format |
| Time | String* | Transaction time in H:MM AM/PM format |
| Payment | String | Cash, Ewallet, or Credit card |
| Cost of goods sold | Float | COGS before tax |
| Gross margin percentage | Float | Fixed at 4.76% for all transactions |
| Gross income | Float | Profit per transaction |
| Customer stratification rating | Float | Customer satisfaction rating (1–10) |

> ⚠️ *Date and Time columns are stored as **text**, not date/time types. Custom calculated fields using `REGEXP_EXTRACT` were required in Looker Studio for time-based analysis.*

### Product Lines

| Product Line | Transactions | Total Revenue |
|---|---|---|
| Food and beverages | 174 | 56,145 |
| Sports and travel | 166 | 55,123 |
| Electronic accessories | 170 | 54,338 |
| Fashion accessories | 178 | 54,306 |
| Home and lifestyle | 160 | 53,862 |
| Health and beauty | 152 | 49,194 |

---

## 🛠️ Key Calculated Fields (Looker Studio)

Since Date and Time are stored as text, standard Looker Studio functions like `PARSE_DATE`, `WEEKDAY`, and `PARSE_TIME` do not work directly. Custom formulas were used instead:

```
-- Extract hour of day from text Time column (e.g., "1:08 PM")
Hour of Day = CAST(REGEXP_EXTRACT(Time, r"^(\d+):") AS NUMBER)
```

**Scorecards with segment filters:**
- **Branch C Revenue** → `SUM(Total)` with Branch = "C" filter applied to scorecard
- **Top Product Line Revenue** → `SUM(Total)` with Product line = "Food and beverages" filter

---

## 🔍 Key Insights

- **Food and Beverages** is the top-performing product line by revenue (56,145) and gross income (2,874)
- **Electronic Accessories** leads in quantity sold (971 units) despite ranking 3rd in revenue
- **Branch C** (Naypyitaw) generates the highest revenue (110,569) and has the highest avg customer rating (7.07)
- Payment methods are nearly evenly split — Ewallet (34.5%), Cash (34.4%), Credit Card (31.1%)
- **Member customers** slightly outperform Normal customers in revenue: 184,223 vs 158,743
- All three cities generate comparable revenue (~106K–111K), suggesting consistent branch performance
- The gross margin is fixed at **4.76%** across all transactions — no pricing variation by category
- Gender split is almost perfectly equal: Female (50.1%) vs Male (49.9%)

---

## 📁 Repository Structure

```
supermarket-sales-dashboard/
│
├── data/
│   └── supermarket_Sales.csv         # Raw dataset (1,000 rows, 17 columns)
│
├── screenshots/
│   ├── page1_executive_sales.png
│   ├── page2_product_operations.png
│   └── page3_customer_payment.png
│
└── README.md
```

---

## 🚀 How to View the Dashboard

1. Open the published dashboard: *[Add your Looker Studio link here]*
2. Use the **Branch**, **City**, and **Product Line** dropdowns to filter by segment
3. The **date range** defaults to Jan 1 – Mar 31, 2019 (full dataset period)
4. Navigate between the 3 pages using the page tabs at the bottom of the report

> Note: Since the dataset covers Q1 2019 only, selecting dates outside this range will show empty charts. The default date range is locked to the data period.

---

## 🧰 Tools & Skills Demonstrated

| Skill | What I did |
|---|---|
| **Looker Studio** | Multi-page dashboard design, scorecards, chart configuration, filter controls |
| **Calculated Fields** | REGEXP_EXTRACT for hour extraction from text-stored time column |
| **Data Visualization** | Chose appropriate chart types for each data dimension |
| **Business Analysis** | Defined KPIs, identified segments, extracted actionable insights |
| **Data Cleaning Awareness** | Identified and handled text-stored date/time columns |

---

## 👩‍💻 About Me

Hi! I'm **Nikita**, an MSc Statistics graduate from Pune, India, building my portfolio as an aspiring **Data Analyst / Data Scientist**.

This project is part of my self-initiated BI work — exploring end-to-end dashboard development from raw CSV data to a multi-page, interactive Looker Studio report.

📂 GitHub: [github.com/nikitagaikwad0111](https://github.com/nikitagaikwad0111)

---

## 📄 Dataset Source

Dataset: [supermarket_Sales.csv](https://github.com/nikitagaikwad0111/supermarket-sales-dashboard/blob/main/data/supermarket_Sales.csv) 
The dataset is included in this repository under the `data/` folder for easy access.

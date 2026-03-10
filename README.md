# 🏦 Consumer Credit Risk & Portfolio Performance Analytics

> An end-to-end credit risk analytics dashboard built in Microsoft Excel to help a banking/financial institution identify high-risk borrowers, understand default drivers, and make smarter lending decisions across a ₹89 Cr+ loan portfolio.

---

## 📸 Dashboard Preview

<img width="1397" height="661" alt="dashboard_preview png" src="https://github.com/user-attachments/assets/c69ac210-c05c-45b3-9aae-51f4bbaccbd4" />


---

## 📌 Table of Contents
- [Business Problem](#-business-problem)
- [Objective](#-objective)
- [Dataset Overview](#-dataset-overview)
- [Approach & Methodology](#-approach--methodology)
- [Key Insights & Findings](#-key-insights--findings)
- [KPIs Tracked](#-kpis-tracked)
- [Dashboard Features](#-dashboard-features)
- [Tools & Techniques](#-tools--techniques)
- [Folder Structure](#-folder-structure)
- [How to Use](#-how-to-use)
- [Author](#-author)

---

## 💼 Business Problem

In the BFSI (Banking, Financial Services & Insurance) sector, **loan defaults are one of the biggest threats to portfolio health**. Lenders face the challenge of approving credit to the right customers while minimizing exposure to borrowers likely to default.

Without a clear, data-driven view of risk patterns, credit officers rely on gut instinct — leading to inconsistent decisions, higher NPAs (Non-Performing Assets), and increased capital provisioning costs.

**The core question this project answers:**
> *Which customers are most likely to default, what factors drive that risk, and how can the portfolio be managed proactively?*

---

## 🎯 Objective

- Build an **interactive Excel dashboard** to monitor credit risk across a ₹89 Cr+ portfolio of 1,700 loan customers
- Identify the **key risk drivers** behind a 33.65% default rate
- Segment customers by risk profile using financial, demographic, and behavioural signals
- Enable dynamic filtering by **Year, City, Employment Status, and Loan Purpose** for drill-down analysis
- Deliver actionable insights for **credit underwriters, risk managers, and portfolio heads**

---

## 📊 Dataset Overview

| Attribute | Detail |
|---|---|
| **Records** | 1,700 customers |
| **Total Portfolio Value** | ₹ 89,23,30,669 |
| **Time Period** | 2022 – 2024 |
| **Geography** | 8 cities, 13 regions |
| **Active Loan Segments** | 6 |
| **Features** | 18 columns |

### Key Variables

| Column | Description |
|---|---|
| `Customer_ID` | Unique customer identifier |
| `Age` | Customer age (range: 21–60) |
| `Annual_Income` | Yearly income in INR (avg: ₹10,91,464) |
| `Employment_Status` | Salaried / Freelancer / Self-Employed / Business |
| `Credit_History_Score` | Credit score (range: 550–849, avg: 700.48) |
| `Debt_to_Income_Ratio` | DTI ratio (range: 0.10–0.60, avg: 0.35) |
| `Loan_Amount` | Loan sanctioned amount in INR |
| `Loan_Term` | Tenure of the loan |
| `Interest_Rate` | Applied interest rate |
| `Loan_Purpose` | Home / Car / Education / Medical / Business / Personal |
| `Loan_Default` | Target variable — 1 = Defaulted, 0 = No Default |
| `City` | City of the applicant (8 cities) |

---

## 🔍 Approach & Methodology

### 1. Data Preparation
- Loaded raw transactional data into the `Raw_Dataset` sheet
- Cleaned and validated 18 fields across 1,700 records with zero formula errors
- Engineered `DTI_Beans` (DTI bucket) column to segment customers by debt burden level
- Extracted `Month` and `Year` from `Application_Date` for time-series analysis

### 2. KPI Computation
- Built a dedicated `KPI's` sheet computing 9 core portfolio metrics
- All metrics auto-update based on slicer selections for dynamic stakeholder reporting

### 3. Chart Layer
- Created 8 purpose-built visualisations in the `Charts` sheet, each addressing a specific risk angle:
  - Age-based portfolio & risk exposure (combo chart)
  - Borrower distribution by profession (bar chart)
  - DTI Inflection Point analysis (sigmoid curve)
  - City-wise risk analysis (dual-axis combo chart)
  - Credit loss distribution by product category
  - Monthly loan disbursement trend with 6-period moving average
  - Portfolio diversification by product (donut chart)
  - Average default rate by month (line chart)

### 4. Dashboard Design
- Assembled a single-screen interactive `Dashboard` with 5 slicers for real-time filtering
- Designed for non-technical stakeholders — clean layout, KPI tiles, and color-coded risk indicators

---

## 💡 Key Insights & Findings

### 🔴 1. Overall Default Rate is Critically High — 33.65%
**1 in 3 borrowers** in this ₹89 Cr portfolio has defaulted. This is well above typical industry benchmarks (5–10%), signalling a structural issue in the credit origination and underwriting process.

---

### 🔴 2. DTI Ratio is the #1 Risk Inflection Point
The **Borrower Repayment Capacity** sigmoid chart reveals that default probability stays low below a DTI of 0.3, then **spikes 5× beyond the critical threshold of ~0.4**.

| DTI Bucket | Default Rate |
|---|---|
| Low (0–20%) | 6.4% |
| Medium (20–40%) | 6.3% |
| **High (40–60%)** | **77.1%** |

> **Recommendation:** Hard-reject or escalate all applications where DTI > 40%.

---

### 🟠 3. Freelancers Carry the Highest Employment Risk
With **448 borrowers and a 38.2% default rate**, Freelancers are both the largest and the riskiest employment segment — driven by income volatility and irregular cash flows.

| Employment Status | Borrowers | Default Rate |
|---|---|---|
| Freelancer | 448 | 38.2% |
| Business | 406 | 34.7% |
| Self-Employed | 422 | 32.7% |
| **Salaried** | **424** | **28.8% ✅** |

> **Recommendation:** Require 12–24 months of bank statements for non-salaried applicants.

---

### 🟠 4. Ahmedabad and Delhi are Geographic Risk Hotspots
The **City-Wise Risk Analysis** dual-axis chart reveals Ahmedabad (**40.6%**) and Delhi (**36.8%**) significantly outpace the portfolio average, while Kolkata (**29.3%**) is the healthiest geography.

| City | Default Rate |
|---|---|
| **Ahmedabad** | **40.6% 🔴** |
| **Delhi** | **36.8% 🔴** |
| Chennai | 34.0% |
| Pune | 33.6% |
| Mumbai | 32.2% |
| Kolkata | **29.3% ✅** |

---

### 🟡 5. Business Expansion Loans Drive the Highest Credit Losses
The **Credit Loss Distribution by Product Category** chart shows Business Expansion (~35.8%) and Education (~35.4%) loans carry the highest default rates, while Home Loans are the safest product at ~30.4%.

| Loan Purpose | Default Rate |
|---|---|
| Business Expansion | 35.8% |
| Education | 35.4% |
| Car Loan | 33.6% |
| Personal Use | 33.4% |
| Medical Emergency | 33.3% |
| **Home Loan** | **30.4% ✅** |

---

### 🟡 6. Portfolio is Evenly Diversified — No Single Concentration Risk
The **Portfolio Diversification** donut chart shows all 6 loan segments cluster tightly between **16–17%** each. While this protects against single-segment shocks, it also means there is no natural hedge from a dominant low-risk segment.

---

### 🟡 7. Default Rate Has Been Rising Year-on-Year
Portfolio credit quality has been deteriorating: **31.3% (2022) → 35.5% (2023) → 34.4% (2024)**. Despite a marginal improvement in 2024, the rate remains well above the 2022 baseline — an early warning signal for portfolio management.

---

### 🟢 8. Mid-Age Segment (31–40) Carries Peak Loan Volume AND Peak Risk
The **Age-Based Portfolio & Risk Exposure** combo chart shows the 31–40 age band holds the largest share of the loan book and the **highest default rate of 0.36** — making it the portfolio's most critical segment for targeted risk monitoring.

---

### ✅ 9. Loan Amount and Income Alone Are Weak Predictors
Defaulted and non-defaulted customers had nearly **identical average loan amounts** (~₹5.25L) and **annual incomes** (~₹10.9L). This confirms that raw income and loan size are insufficient screening criteria — **DTI ratio and credit history score are far more predictive signals.**

---

## 📈 KPIs Tracked

| KPI | Value |
|---|---|
| **Total Customers** | 1,700 |
| **Total Portfolio Value** | ₹ 89,23,30,669 |
| **Overall Default Rate** | 33.65% |
| **Average Credit Score** | 700.48 |
| **Average Interest Rate** | Tracked dynamically |
| **Total Cities** | 8 |
| **Average DTI** | 0.35 |
| **Average Annual Income** | ₹ 10,91,464 |
| **Active Loan Segments** | 6 |

---

## 🖥 Dashboard Features

| Feature | Description |
|---|---|
| **9 KPI Tiles** | Top-row metrics with icons, auto-updating with slicers |
| **5 Interactive Slicers** | Filter by Employment Status, Application Date, Year, Loan Purpose, City |
| **Age-Based Risk Chart** | Combo chart: loan volume vs. default rate across 4 age bands |
| **Profession Distribution** | Borrower count by employment type (bar chart) |
| **DTI Inflection Curve** | Sigmoid chart highlighting the 5× risk threshold at DTI ~0.4 |
| **City-Wise Risk Analysis** | Dual-axis: loan volume + default rate per city |
| **Credit Loss by Product** | Default rate comparison across all 6 loan categories |
| **Monthly Disbursement Trend** | Line chart with 6-period moving average overlay |
| **Portfolio Diversification** | Donut chart — product mix breakdown by loan purpose |
| **Monthly Default Rate** | Seasonality analysis of defaults across Jan–Dec |

---

## 🛠 Tools & Techniques

| Tool / Feature | Usage |
|---|---|
| **Microsoft Excel** | Core platform |
| **Pivot Tables** | Aggregations powering all KPIs and chart data sources |
| **Pivot Charts** | 8 purpose-built visualisations |
| **Slicers** | 5 interactive filters for dynamic analysis |
| **Combo / Dual-Axis Charts** | Simultaneous volume and rate comparison |
| **Sigmoid Curve Chart** | DTI inflection point and repayment capacity modelling |
| **Donut Chart** | Portfolio product diversification view |
| **Moving Average Overlay** | 6-period trend smoothing on monthly disbursements |
| **Conditional Formatting** | Color-coded KPI tiles and risk indicators |
| **Feature Engineering** | DTI bucketing for custom risk segmentation |

---

## 📁 Folder Structure

```
bfsi-credit-risk-dashboard/
│
├── README.md
├── LICENSE
├── data/
│   └── raw/
│       └── credit_risk_customers_raw.xlsx
│
├── dashboard/
│   └── credit_risk_customers_Dashboard.xlsx   ⭐ Main deliverable
│
└── docs/
    ├── dashboard_preview.png                   ← Screenshot embedded above
    └── data_dictionary.md
```

---

## ▶️ How to Use

1. **Clone the repository**
   ```bash
   git clone https://github.com/Shivam98-cd/bfsi-credit-risk-dashboard.git
   ```

2. **Open the dashboard**
   - Navigate to `dashboard/credit_risk_customers_Dashboard.xlsx`
   - Open in **Microsoft Excel 2016 or later** (slicers require a modern version)
   - Enable editing if prompted

3. **Interact with the dashboard**
   - Use the **5 slicers** (Employment Status, Date, Year, Loan Purpose, City) to filter dynamically
   - All 9 KPI tiles and 8 charts update in real time based on your selection

4. **Explore underlying data**
   - `Raw_Dataset` — 1,700 rows of raw customer loan data
   - `KPI's` — computed portfolio metrics
   - `Charts` — pivot tables and data powering each visualisation

---

## 👤 Author

**[Shivam Yadav]**  
Data Analyst | BFSI Domain

[![LinkedIn](https://img.shields.io/badge/LinkedIn-Connect-blue?logo=linkedin)](www.linkedin.com/in/shivam-yadav98)
[![GitHub](https://img.shields.io/badge/GitHub-Follow-black?logo=github)](https://github.com/Shivam98-cd)

---

> ⭐ If you found this project useful, please consider starring the repository — it helps others discover it!

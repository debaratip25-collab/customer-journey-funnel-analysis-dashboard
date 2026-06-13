# 📊 Customer Journey & Funnel Analysis Dashboard

> **A complete, industry-oriented, job-ready Business Analyst portfolio project built in Microsoft Power BI.**

![Power BI](https://img.shields.io/badge/Tool-Power%20BI-F2C94C?style=for-the-badge&logo=powerbi&logoColor=black)
![Excel](https://img.shields.io/badge/Tool-Excel-217346?style=for-the-badge&logo=microsoftexcel&logoColor=white)
![DAX](https://img.shields.io/badge/Language-DAX-2E75B6?style=for-the-badge)
![Domain](https://img.shields.io/badge/Domain-Marketing%20Analytics-1F3864?style=for-the-badge)
![Level](https://img.shields.io/badge/Level-Beginner%20to%20Intermediate-green?style=for-the-badge)

---

## 📌 Project Objective

Track customer behaviour across the full buying journey — from first website visit through to purchase and post-purchase retention — and identify the funnel stages, channels, and segments that drive the most conversion and revenue loss.

---

## 🧩 Business Problem

The marketing team lacked visibility into:
- Where in the funnel customers are dropping off
- Which acquisition channels deliver the best conversion ROI
- Which customer segments generate the most revenue
- Why the overall conversion rate is below the 15% industry benchmark

Without this data, budget decisions were guesswork and high-value customer segments were being under-invested.

---

## 📁 Repository Structure

```
customer-journey-funnel-analysis-dashboard/
│
├── data/
│   └── CustomerJourneyData.csv          ← 150-row dataset, 20 columns
│
├── dashboard/
│   └── CustomerJourneyFunnelDashboard.pbit  ← Power BI Template file
│
├── excel/
│   └── CJ_Excel_Analysis.xlsx           ← 9-sheet Excel analysis workbook
│
├── documentation/
│   ├── CustomerJourney_FunnelAnalysis_Project.docx  ← Full project document
│   └── CJ_Recommendations_Report.docx   ← Business recommendations report
│
├── screenshots/
│   ├── 01_KPI_Overview.png
│   ├── 02_Funnel_Analysis.png
│   ├── 03_Channel_Performance.png
│   ├── 04_Segment_Analysis.png
│   └── 05_Retention_Dashboard.png
│
└── README.md
```

---

## 🗃️ Dataset Overview

| Property | Details |
|---|---|
| Total Records | 150 customer interaction rows |
| Total Columns | 20 fields |
| Date Range | January 2024 – December 2024 |
| Acquisition Channels | 7 (Organic Search, Paid Search, Social Media, Email Campaign, Referral, Direct, Display Ad) |
| Customer Segments | 5 (Premium, Standard, Basic, Enterprise, SMB) |
| Regions | 5 (North, South, East, West, Central) |
| Funnel Stages | 5 (Awareness, Interest, Consideration, Intent, Purchase) |
| File Format | CSV |

### Key Columns

| Column | Type | Description |
|---|---|---|
| Customer ID | Text | Unique identifier |
| Customer Segment | Text | Premium / Standard / Basic / Enterprise / SMB |
| Acquisition Channel | Text | Source of website visit |
| Website Visit Date | Date | Date of interaction |
| Add to Cart | Yes/No | Cart engagement flag |
| Checkout Started | Yes/No | Checkout initiation flag |
| Purchase Completed | Yes/No | Conversion flag |
| Purchase Value (INR) | Decimal | Revenue generated |
| Session Duration | Integer | Time on site in seconds |
| Funnel Stage | Text | Furthest stage reached |
| Conversion Status | Text | Converted / Not Converted |
| Customer Retention Status | Text | Retained / Churned |

---

## 📐 Funnel Framework

```
┌─────────────────────────────────────────────────┐
│  Total Visitors → 100%                          │
│        │                                        │
│  Add to Cart → 56%                              │
│        │                                        │
│  Checkout Started → 27.3%                       │
│        │                                        │
│  Purchase Completed → 10.0%  ← Conversion Rate  │
└─────────────────────────────────────────────────┘
```

**The 5 Stages:**
1. **Awareness** — Customer discovers brand via channel/ad/search
2. **Interest** — Customer browses website and views products
3. **Consideration** — Customer adds item to cart (high intent signal)
4. **Intent** — Customer initiates checkout process
5. **Purchase** — Customer completes transaction

---

## 📊 DAX Measures Built (20+)

```dax
-- Core Conversion KPIs
Total Visitors        = COUNTROWS(CustomerJourneyData)
Total Converted       = COUNTROWS(FILTER(CustomerJourneyData, [Conversion Status] = "Converted"))
Conversion Rate       = DIVIDE([Total Converted], [Total Visitors], 0)
Add to Cart Rate      = DIVIDE([Add to Cart Count], [Total Visitors], 0)
Checkout Rate         = DIVIDE([Checkout Count], [Total Visitors], 0)
Funnel Drop-off Rate  = 1 - [Conversion Rate]

-- Revenue KPIs
Total Revenue         = SUM(CustomerJourneyData[Purchase Value])
Average Purchase Value = AVERAGEX(FILTER(..., [Purchase Completed] = "Yes"), [Purchase Value])
Revenue per Customer  = DIVIDE([Total Revenue], [Total Converted], 0)

-- Engagement & Retention
Customer Retention Rate = DIVIDE([Retained Count], [Total Visitors], 0)
Bounce Rate             = DIVIDE([Bounce Count], [Total Visitors], 0)
Avg Feedback Score      = AVERAGE(CustomerJourneyData[Customer Feedback Score])
Avg Session Duration    = AVERAGE(CustomerJourneyData[Session Duration])

-- Funnel Stage Counts
Awareness Count     = COUNTROWS(FILTER(..., [Funnel Stage] = "Awareness"))
Interest Count      = COUNTROWS(FILTER(..., [Funnel Stage] = "Interest"))
Consideration Count = COUNTROWS(FILTER(..., [Funnel Stage] = "Consideration"))
Intent Count        = COUNTROWS(FILTER(..., [Funnel Stage] = "Intent"))
Purchase Count      = COUNTROWS(FILTER(..., [Funnel Stage] = "Purchase"))
```

---

## 🖥️ Dashboard Layout

```
┌──────────────────────────────────────────────────────────┐
│     Customer Journey & Funnel Analysis Dashboard          │
├──────────┬──────────┬──────────┬──────────┬──────────────┤
│ Visitors │ Conv Rate│ Revenue  │ Retention│ Drop-off Rate│  ← KPI Cards
├──────────┴──────────┴──────────┴──────────┴──────────────┤
│ Funnel Chart   │  Channel Bar Chart  │  Monthly Trend    │  ← Middle Row
├────────────────┴─────────────────────┴───────────────────┤
│ Segment Matrix │  Retention Donut    │  Region Bar Chart │  ← Bottom Row
├──────────────────────────────────────────────────────────┤
│ Slicers: Channel | Segment | Region | Date | Stage       │
└──────────────────────────────────────────────────────────┘
```

**Visuals included:**
- 6 KPI Cards (navy/gold theme)
- Funnel Chart — 5-stage drop-off visualisation
- Clustered Bar Chart — Conversion rate by acquisition channel
- Line & Clustered Column Chart — Monthly visitors and conversion trend
- Matrix Visual — Segment performance (Conversion Rate, Revenue, Retention)
- Donut Chart — Customer retention status breakdown
- Stacked Bar Chart — Funnel stage distribution by region
- 5 Slicers — Channel, Segment, Region, Date Range, Funnel Stage

---

## 📈 Key Insights

| # | Insight | Impact |
|---|---|---|
| 1 | Checkout stage has a **63% abandonment rate** — the single largest revenue leak | HIGH |
| 2 | **Email Campaign** delivers the highest conversion rate across all 7 channels | HIGH |
| 3 | **Premium segment** = ~20% of visitors but 60%+ of total revenue | HIGH |
| 4 | **Social Media** drives the most traffic but the lowest conversion rate | MEDIUM |
| 5 | **North region** consistently outperforms all other regions in conversion | MEDIUM |
| 6 | **Retained customers** give 3x higher feedback scores than churned customers | MEDIUM |

---

## 💡 Business Recommendations

| Priority | Recommendation | Expected Benefit |
|---|---|---|
| HIGH | One-click checkout + trust badges on cart page | Conv Rate +15–20% |
| HIGH | Personalised retargeting by funnel stage + abandoned cart emails | Revenue +20% |
| HIGH | Reallocate Social Media budget to Email and Referral channels | CAC -25% |
| MEDIUM | Post-purchase NPS survey + 7-day customer success email | CSAT 6.2 → 8.0+ |
| MEDIUM | Loyalty email sequence + referral reward programme | Retention +20% |
| MEDIUM | Premium VIP programme with exclusive access and discounts | Revenue +15% |
| LOW | A/B test product page layout, CTA copy, and social proof | ATC Rate +10% |
| LOW | Email capture popups with lead magnets on landing pages | Email Conv +30% |

---

## 🗂️ Excel Workbook — Sheet Guide

The `CJ_Excel_Analysis.xlsx` file contains 9 sheets mirroring a professional business process analytics workbook:

| Sheet | Contents |
|---|---|
| **Customer Journey Data** | Full 150-row raw dataset with 3 calculated columns and conditional formatting |
| **KPI Summary** | KPI blocks, funnel analysis table, and channel quick-view — colour-coded |
| **Channel Analysis** | All 7 channels with 17 performance metrics and performance tier labels |
| **Segment Analysis** | All 5 segments with conversion, revenue, retention, and revenue share |
| **Funnel SLA Dashboard** | Per-customer SLA target vs achieved with MET/BREACH status + channel summary |
| **Revenue Analysis** | Revenue breakdown by Channel, Segment, and Product Viewed |
| **Bottleneck Analysis** | Top 30 non-converting customers with bottleneck points + improvement opportunity tags |
| **Drop-off Analysis** | Stage-by-stage drop-off rates broken down by both Channel and Segment |
| **Recommendations** | 8 prioritised recommendations + 4-phase implementation roadmap |

---

## 🔧 How to Use This Project

### Step 1 — Load the Dataset
1. Open Power BI Desktop
2. Click **Home → Get Data → Text/CSV**
3. Select `CustomerJourneyData.csv`
4. Click **Transform Data** and verify column types
5. Click **Close & Apply**

### Step 2 — Open the Template
1. Open `CustomerJourneyFunnelDashboard.pbit`
2. When prompted, point to `CustomerJourneyData.csv`
3. All DAX measures and report layout will load automatically

### Step 3 — Explore the Dashboard
- Use slicers to filter by Channel, Segment, Region, Date, and Funnel Stage
- Cross-filter visuals by clicking any chart element
- Hover over bars and cards for detailed tooltips

### Step 4 — Explore the Excel Workbook
- Open `CJ_Excel_Analysis.xlsx` in Microsoft Excel
- Navigate sheets using the colour-coded tab bar
- All data is pre-computed — no setup required

---

## 🛠️ Tools & Technologies

| Tool | Purpose |
|---|---|
| Microsoft Power BI Desktop | Dashboard development and DAX measure creation |
| DAX (Data Analysis Expressions) | KPI calculations and funnel metrics |
| Power Query (M Language) | Data loading, type casting, and transformation |
| Microsoft Excel (openpyxl) | Multi-sheet analysis workbook |
| Python (openpyxl library) | Excel workbook generation and formatting |
| CSV | Raw dataset format |

---

## 📚 Business Analysis Skills Demonstrated

- ✅ Customer Journey Mapping (5-stage AICP framework)
- ✅ Funnel Analysis (stage-to-stage conversion measurement)
- ✅ KPI Definition and DAX implementation (20+ measures)
- ✅ Customer Segmentation (demographic + commercial)
- ✅ Conversion Rate Optimisation analysis
- ✅ Retention Analysis (Retained vs Churned)
- ✅ Root Cause Analysis (channel and stage-level drill-down)
- ✅ Business Recommendations (8 prioritised with timelines)
- ✅ Dashboard Design (professional corporate theme)
- ✅ Stakeholder-ready reporting

---

## 💼 Resume Bullet Points

**One-liner:**
> Built Power BI Customer Journey & Funnel Analysis Dashboard | 150 customer interactions | 20+ DAX KPIs | Identified 63% checkout abandonment | Delivered 8 business recommendations

**Full version:**
> Designed and built an end-to-end Customer Journey & Funnel Analysis Dashboard in Microsoft Power BI. Analysed a 150-row customer interaction dataset across 20 dimensions including acquisition channels, funnel stages, demographics, and purchase behaviour. Created 20+ DAX measures, a 5-stage conversion funnel, a 9-sheet Excel analysis workbook, and a formal Recommendations Report — identifying a 63% checkout abandonment rate and recommending targeted interventions estimated to improve conversion rates by 15–20%.

---

## 🙋 About This Project

This project was created as a portfolio piece demonstrating end-to-end Business Analyst skills — from data collection and cleaning through to visualisation, insight generation, and business recommendations.

**Prepared by:** Debarati
**Date:** June 2026
**Domain:** Marketing Analytics, E-Commerce, Customer Experience
**Level:** Beginner to Intermediate

---

## 📬 Connect

If you found this project helpful, feel free to ⭐ star the repository and connect on LinkedIn!

---

*Built with 💙 using Power BI, DAX, Excel, and Python*

# IMS StepUp SA — Marketing Analytics Dashboard

> End-to-end marketing analytics solution for a South African footwear retailer.  
> A 4-page executive Power BI dashboard covering campaign ROI, sales performance,  
> customer segmentation & CLV, and website analytics — powered by Python and DAX  
> across 24 months of real business data.

![Python](https://img.shields.io/badge/Python-3.10-blue?style=flat-square)
![Power BI](https://img.shields.io/badge/Power%20BI-Dashboard-yellow?style=flat-square)
![DAX](https://img.shields.io/badge/DAX-Measures-orange?style=flat-square)
![Pandas](https://img.shields.io/badge/Pandas-Data%20Cleaning-lightgrey?style=flat-square)
![Status](https://img.shields.io/badge/Status-Complete-brightgreen?style=flat-square)

---

## Overview

IMS StepUp SA is a South African footwear retailer. This project delivers a full marketing analytics pipeline — from raw data cleaning in Python through to a polished executive dashboard in Power BI — enabling the business to make data-driven decisions across marketing spend, store performance, customer value, and digital channels.

**Scope:** 24 months of real business data across campaigns, transactions, customer records, and GA4 web analytics.

---

## Dashboard Pages

### Page 1 — Campaign ROI & Marketing Performance
- Total spend vs. revenue generated per campaign
- Return on ad spend (ROAS) by channel
- Campaign cost-per-acquisition (CPA) trends
- Month-over-month campaign performance comparison

### Page 2 — Store & Product Sales
- Revenue and units sold by store location
- Top and bottom performing product categories
- Sales trends over 24 months
- Seasonal performance patterns

### Page 3 — Customer Segmentation & CLV
- RFM-based customer segmentation (Recency, Frequency, Monetary)
- Customer Lifetime Value (CLV) distribution across segments
- High-value vs. at-risk customer identification
- Segment-level revenue contribution

### Page 4 — Website Performance (GA4)
- Sessions, users, bounce rate, and conversion rate
- Traffic source breakdown (organic, paid, direct, referral)
- Landing page performance
- Online-to-store attribution trends

---

## Technical Approach

### Data Cleaning (Python)
- Ingested and merged multiple raw data sources (transactions, campaigns, customer records, GA4 export)
- Handled missing values, duplicate records, and inconsistent date/category formatting
- Standardised customer IDs across datasets to enable cross-page analysis
- Exported cleaned `.csv` files as Power BI data sources

### Data Modelling (Power BI)
- Built a star schema model linking fact tables (sales, sessions) to dimension tables (customers, products, campaigns, dates)
- Created a date dimension table for consistent time intelligence across all pages

### DAX Measures
Key measures built include:

```dax
-- Campaign ROAS
ROAS = DIVIDE([Total Revenue], [Total Ad Spend], 0)

-- Customer Lifetime Value
CLV = SUMX(Customers, [Avg Order Value] * [Purchase Frequency] * [Customer Lifespan])

-- Month-over-Month Growth
MoM Growth % = 
DIVIDE(
    [Revenue This Month] - [Revenue Last Month],
    [Revenue Last Month],
    0
)
```

### Customer Segmentation
- RFM scoring applied in Python (Pandas) to classify customers into segments: Champions, Loyal, At Risk, Lost
- Segment labels imported into Power BI as a dimension for cross-filter analysis

---

## Repository Structure

```
ims-stepup-sa/
├── data/
│   ├── raw/                  # Original source data
│   └── cleaned/              # Python-processed output files
├── notebooks/
│   └── data_cleaning.ipynb   # Python cleaning and RFM segmentation
├── powerbi/
│   └── StepUp_Dashboard.pbix # Full 4-page Power BI dashboard
├── dax/
│   └── measures.md           # All DAX measure definitions
└── README.md
```

---

## How to Run

```bash
# Clone the repo
git clone https://github.com/Toni8/<repo-name>.git
cd ims-stepup-sa

# Install Python dependencies
pip install pandas numpy matplotlib seaborn jupyter

# Run the cleaning notebook
jupyter notebook notebooks/data_cleaning.ipynb
```

To view the dashboard, open `powerbi/StepUp_Dashboard.pbix` in Power BI Desktop.

> Note: Source data has been anonymised where required to protect business confidentiality.

---

## Key Business Insights Delivered

| Area | Insight |
|---|---|
| Campaigns | Identified highest and lowest ROAS channels across 24 months |
| Products | Pinpointed top revenue-driving categories by store |
| Customers | Segmented customer base by lifetime value for targeted retention |
| Website | Linked GA4 traffic sources to in-store and online conversion |

---

## Tech Stack

`Python` · `Pandas` · `Power BI` · `DAX` · `GA4` · `Matplotlib` · `Seaborn` · `Excel`

---

*Built by [Sihle Kalolo](https://github.com/Toni8) · [Portfolio](https://sihle-kalolo-portfolio.vercel.app/)*

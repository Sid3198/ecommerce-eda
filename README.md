# Exploratory Data Analysis — E-commerce Dataset

End-to-end EDA on a UK-based online retailer's transaction data, performed in Python using Pandas and Matplotlib. Covers data cleaning, revenue analysis, seasonal trends, and market concentration.

![Monthly Sales Trend](charts/monthly_sales_trend.png)

## Objective

Perform end-to-end exploratory data analysis to identify sales trends, top-performing products, and revenue distribution across markets, producing a structured report suitable for business stakeholders.

## Tools Used

- **Python** — core language
- **Pandas** — data cleaning, transformation, and aggregation
- **Matplotlib** — data visualization

## Dataset

- **Source:** E-Commerce Data (UK online retailer transactions), Kaggle
- **Size:** 541,909 transactions, Dec 2010 – Dec 2011
- **Fields:** InvoiceNo, StockCode, Description, Quantity, InvoiceDate, UnitPrice, CustomerID, Country

## Data Cleaning

- Loaded the dataset with `ISO-8859-1` encoding to correctly handle special characters (e.g., £ symbol)
- Identified and removed **cancelled orders** (negative Quantity values, InvoiceNo prefixed with "C")
- Identified and removed rows with **missing CustomerID** (~25% of the dataset — these can't support customer-level analysis)
- Removed **duplicate rows**
- Created a `TotalPrice` column (`Quantity × UnitPrice`) for revenue analysis
- **Result:** cleaned dataset from 541,909 → 392,732 valid transaction records

## Key Findings

**1. Data Quality:** ~25% of transactions had missing Customer IDs and ~10,000 were cancelled orders. After cleaning, 392,732 valid records remained for analysis.

**2. Top Products:** "Paper Craft, Little Birdie" was the top revenue-generating product (£168,469.60), followed by the Regency Cakestand 3 Tier (£142,264.75).

![Top 10 Products by Revenue](charts/top_products.png)

**3. Seasonal Trend:** Revenue grew steadily through the year, peaking in November 2011 (£1.16M) — consistent with pre-holiday shopping demand. The December figure reflects an incomplete month of data rather than an actual decline.

**4. Market Concentration:** The UK accounted for **81.97%** of total revenue (£7.29M of £8.89M total), despite the business serving 38 countries — indicating a heavily domestic customer base with limited international penetration.

![Top 10 Countries by Revenue](charts/top_countries.png)

## Recommendations

- Focus marketing spend around the Sep–Nov period to capitalize on the pre-holiday demand surge
- Investigate low international revenue share — targeted campaigns in high-potential secondary markets (Netherlands, Germany) could help diversify revenue
- Prioritize inventory planning around top-selling SKUs identified in this analysis

## Repo Structure

```
ecommerce-eda/
├── README.md
├── ecommerce_eda.ipynb
└── charts/
    ├── top_products.png
    ├── monthly_sales_trend.png
    └── top_countries.png
```

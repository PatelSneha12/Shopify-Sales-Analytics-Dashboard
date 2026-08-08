# Shopify Sales Analytics Dashboard

An end-to-end analytics project for a Shopify store (**FragsTalk**, a perfume/fragrance decant brand) — from raw Shopify data exports, through Python data cleaning, to a multi-page interactive Power BI dashboard covering sales, customers, products and time-based order patterns.

## Business Problem

Shopify's native reporting only goes so far. This project consolidates raw order, product and customer exports into a clean, unified model and turns them into a decision-ready dashboard — tracking revenue, order volume, customer retention, product/brand performance and when customers are actually buying.

## Data Sources

Raw Shopify exports (`.xls`):
- `order1.xls` — order-level transaction data (order name, email, financial/fulfillment status, amounts, shipping address, timestamps)
- `products_export_1.xls` — product catalog (handle, title, description, vendor/brand, etc.)
- `customers_export.xls` — customer records (name, email, marketing consent, address, total spent, total orders)

## Data Cleaning (Python / Pandas)

`Untitled.ipynb` documents the full cleaning pipeline:

- Loaded the three raw exports into Pandas DataFrames
- Dropped fully-empty columns and duplicate rows
- Checked and handled missing values — dropped sparse columns (>50% null) and filled remaining text nulls
- Parsed `Created at` into proper datetime and engineered `Year`, `Month`, `Day`, `hour` and `Pdate` columns for time-based analysis
- Standardized shipping address fields (city, province, country) to uppercase for consistent grouping
- Checked for duplicate customer emails
- Exported cleaned datasets back out as CSVs for use in Power BI

## Dashboard (Power BI)

`dashboard filter.pbix` is a multi-page report with global filter/navigation buttons, date-preset slicers and custom visuals (Tornado Chart, Table Heat Map, Scrolling Text, and more):

- **Overview** — revenue, total orders, new customers and lost customers KPI cards, a trend line, and a filterable summary table
- **Sales Overview** — current-month orders and revenue, order/revenue trend chart, and top-brand/product breakdowns
- **Time Analysis** — busiest hour, highest-order weekday, weekend-vs-weekday and time-of-day order patterns
- **Product** — distinct brands and products, average revenue per product, revenue per brand, and top-N brand ranking
- **Customer** — unique customers, returning customers, and revenue by customer type/segment

All pages share a consistent set of slicers (date presets, region, customer type, billing name) so any page can be filtered the same way.

## Tech Stack

- **Python** — data cleaning (`Untitled.ipynb`)
- **Pandas** — data wrangling and feature engineering
- **Power BI** — dashboard, data modeling and DAX measures

## Project Structure

```
Shopify-Sales-Analytics-Dashboard/
├── order1.xls                  # raw Shopify order export
├── products_export_1.xls       # raw Shopify product export
├── customers_export.xls        # raw Shopify customer export
├── Untitled.ipynb              # Python data cleaning notebook
├── dashboard filter.pbix       # Power BI dashboard
└── README.md
```

## How to Run

**Data cleaning:**
```bash
git clone https://github.com/PatelSneha12/Shopify-Sales-Analytics-Dashboard.git
cd Shopify-Sales-Analytics-Dashboard
pip install pandas numpy jupyter
jupyter notebook Untitled.ipynb
```

**Dashboard:**
Open `dashboard filter.pbix` in [Power BI Desktop](https://www.microsoft.com/en-us/power-platform/products/power-bi/downloads).

> Note: the notebook currently reads/writes CSVs from hardcoded local paths (`order1.csv`, `products_export_1.csv`, `customers_export.csv`, and an output path under `C:\Users\...`). Update these paths — and export the `.xls` files to `.csv` first — before re-running.

## Author

**Sneha Patel**
Data Analyst | Business Analytics Enthusiast
[LinkedIn](https://www.linkedin.com/in/snehapatel1212) · [GitHub](https://github.com/PatelSneha12)

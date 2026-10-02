# 🛒 Olist E-Commerce Sales & Customer Analytics

An interactive e-commerce analytics project built with **Microsoft Excel and Power Query**, exploring sales performance, customer behavior, product categories, payment methods, and customer reviews.

This is my third Data Analytics project, and the first where I moved past single-table dashboards into working with **multiple related datasets, real data transformation, and data modeling**.

<img width="1384" height="860" alt="Screenshot 2026-10-02 001549" src="https://github.com/user-attachments/assets/9d967065-96a6-47b5-8a5c-c720c6aa5dfa" />


---

## 📌 Project Overview

E-commerce businesses generate data from a lot of different places — orders, customers, products, sellers, payments, reviews. The hard part isn't having the data, it's connecting it into something that actually explains the business.

For this project I used the **Olist Brazilian E-Commerce dataset** to build an interactive Excel dashboard that answers questions like:

- How are sales changing over time?
- Which product categories generate the most revenue?
- Where are customers located?
- Which payment methods are used most often?
- How are customers rating their purchases?
- Which states generate the most revenue?
- How many orders and items are being handled?

The goal was to practice the full workflow: **raw data → cleaning → transformation → analysis → visualization → dashboard.**

---

## 🎯 Project Objectives

- Work with a real-world, multi-table e-commerce dataset
- Clean and transform data using Power Query
- Combine related datasets using common keys
- Build meaningful business metrics
- Analyze sales and customer behavior
- Create PivotTables and PivotCharts
- Build an interactive, slicer-driven Excel dashboard
- Get better at presenting analytical findings clearly

---

## 🗂️ Dataset

Built on the **Brazilian E-Commerce Public Dataset by Olist**, which covers orders, customers, products, sellers, payments, and reviews.

| File | Purpose |
|---|---|
| `olist_orders_dataset.csv` | Order information and order status |
| `olist_order_items_dataset.csv` | Products purchased in each order |
| `olist_products_dataset.csv` | Product information |
| `olist_customers_dataset.csv` | Customer information and location |
| `olist_order_payments_dataset.csv` | Payment information |
| `olist_order_reviews_dataset.csv` | Customer review scores |
| `olist_sellers_dataset.csv` | Seller information |
| `product_category_name_translation.csv` | Portuguese → English category names |

I left out the geolocation file (around 1 million rows) since it wasn't needed for the analyses in this dashboard.

---

## 🔄 Data Preparation with Power Query

This project was really where I got comfortable with Power Query instead of manually cleaning each dataset by hand.

**What I did, step by step:**

1. Imported the required CSVs into Excel via Power Query
2. Checked and corrected data types
3. Cleaned and prepared each dataset individually
4. Created a calculated `Total_Item_Value` column
5. Merged order items with product information
6. Added English category names using the translation table
7. Merged in order dates and customer IDs
8. Connected customer information to order data
9. Added seller information
10. Created an `Order Month` field for monthly analysis
11. Calculated delivery duration
12. Created a `Delivery Status` field
13. Loaded the cleaned master dataset into Excel for analysis

```text
Total_Item_Value = price + freight_value
```

Delivery time was calculated as the number of days between purchase date and actual delivery date, where that data was available.

---

## 📊 Key Business Metrics

| Metric | Value | Notes |
|---|---|---|
| Total Orders | 99,441 | Total order count in the dataset |
| Total Revenue | R$13.59 million | `SUM(price)` from order items — freight and payment values were kept separate |
| Average Order Value | ≈ R$136.65 | Total Revenue ÷ Total Orders |
| Total Items Sold | 112,650 | Total order-item records |
| Average Items per Order | ≈ 1.13 | Items Sold ÷ Total Orders |
| Total Customers | 96,096 | Unique customers, via `customer_unique_id` |
| Average Review Score | ≈ 4.09 / 5 | Mean customer review score |

---

## 📈 Dashboard

The dashboard was built to give a quick overview of the business while still letting the user dig into specifics.

**KPI cards:** Total Orders · Total Revenue · Total Customers · Review Score · Items Sold

**Visualizations:**

1. **Monthly Sales Trend** — line chart showing how sales moved over time, useful for spotting peaks and slow periods
2. **Top Product Categories** — horizontal bar chart of the categories driving the most revenue
3. **Customers by State** — geographic comparison of unique customers across Brazilian states
4. **Payment Method Usage** — doughnut chart covering Credit Card, Boleto, Voucher, Debit Card, and Not Defined
5. **Customer Review Score** — column chart showing the distribution of 1–5 star ratings
6. **Sales by Customer State** — horizontal bar chart connecting customer geography to revenue

---

## 🎛️ Interactive Filters

Five slicers make the dashboard explorable without touching the PivotTables directly:

- Customer State
- Seller State
- Payment Type
- Product Category
- Order Status

Select a product category, for example, and the sales, customer, and review numbers all update to match.

---

## 📊 Additional Analysis

Not everything made it onto the main dashboard. The workbook's **PivotTables** sheet also holds supporting analysis for deeper exploration:

- Sales by Seller State
- Order Status Distribution
- Average Delivery Days by Customer State
- Monthly Sales
- Product Category Performance
- Customer State Analysis
- Payment Analysis
- Review Analysis

---

## 🧮 Calculation Decisions Worth Explaining

A few choices mattered more than they might look like on the surface:

**Revenue** — I used `SUM(price)` from the order-items dataset rather than `payment_value`, since an order can have multiple payment records and `payment_value` reflects payment transactions, not product-level sales.

**Customers** — Total customers was calculated using `customer_unique_id` rather than raw customer records, to avoid double-counting people who placed more than one order.

**Reviews** — Review scores were analyzed on their own rather than merged into every order-item row, since that would have duplicated review data unnecessarily across the master table.

---

## 🛠️ Tools & Technologies

**Microsoft Excel** — Formulas, Excel Tables, PivotTables, PivotCharts, Slicers, Dashboard Design, KPI Cards

**Power Query** — Data Import, Data Cleaning, Type Transformation, Dataset Merging, Column Creation, Master Dataset Preparation

---

## 📁 Repository Structure

```text
Olist-Ecommerce-Sales-Customer-Analytics/
│
├── Olist_Ecommerce_Analytics.xlsx
│
├── Raw Data/
│   ├── olist_customers_dataset.csv
│   ├── olist_geolocation_dataset.csv
│   ├── olist_order_items_dataset.csv
│   ├── olist_order_payments_dataset.csv
│   ├── olist_order_reviews_dataset.csv
│   ├── olist_orders_dataset.csv
│   ├── olist_products_dataset.csv
│   ├── olist_sellers_dataset.csv
│   └── product_category_name_translation.csv
│
└── images/
    └── dashboard-full.png
```

---

## 📑 Workbook Structure

| Sheet | Contents |
|---|---|
| **Dashboard** | KPI cards, charts, slicers, and key business metrics |
| **Analysis** | Main KPI calculations and supporting formulas |
| **PivotTables** | PivotTables and PivotCharts behind the dashboard, plus extra analysis |
| **Clean Data** | The cleaned, merged dataset produced by Power Query |

---

## 💡 What I Learned

This project was tougher than my earlier Excel dashboards, mainly because I was working across multiple related datasets instead of one clean table.

**Working with multiple datasets** — real analytics rarely starts with a single, perfectly organized table. Information lives in different places and has to be connected correctly.

**Power Query** — hands-on practice importing, transforming, merging queries, expanding columns, and building calculated fields.

**Data modeling decisions** — merging everything together isn't always right. Payment and review tables can contain multiple records per order, and joining them carelessly duplicates data.

**Choosing the right metric** — understanding what a column actually represents matters as much as knowing how to calculate it. `price`, `freight_value`, and `payment_value` are not interchangeable, even though they all sound like "money."

**Dashboard restraint** — I spent real time deciding what *not* to show. Instead of cramming in every possible chart, I kept a smaller set that each adds a different perspective.

---

## 🚧 Challenges I Ran Into

This wasn't just chart-building — there were a few real troubleshooting moments.

One was the category translation merge: duplicate column names appeared during the Power Query merge, and the wrong category column was being expanded at first. I had to step back through the query, find the bad transformation, remove it, and rebuild the merge properly.

Another was calculating delivery days while handling orders that hadn't been delivered yet — those needed to be excluded rather than throwing off the average.

Honestly, these problems taught me more than the charts did. They're the kind of thing you only run into with messy, real datasets rather than tutorial-clean ones.

---

## 📌 Key Takeaways

The workflow I followed, end to end:

```text
Raw Data → Data Cleaning → Power Query Transformation → Dataset Merging
→ Data Validation → KPI Calculations → PivotTables → PivotCharts
→ Interactive Dashboard → Business Insights
```

The biggest lesson: good analytics starts with good data preparation. A dashboard can look impressive, but if the data behind it isn't correct, the visuals don't mean much.

---

## 🚀 Future Improvements

- Rebuild the analysis in Tableau and Power BI
- Go deeper on customer segmentation
- Analyze repeat-purchase behavior
- Dig further into delivery performance
- Reproduce the analytical queries in SQL
- Run exploratory data analysis in Python

---

## 📚 Dataset Source

This project uses the public **Brazilian E-Commerce Public Dataset by Olist**. The analysis and dashboard here are an independent learning project and are not affiliated with or endorsed by Olist.

---

## 👨‍💻 About This Project

This is a personal Data Analytics project built to get real, practical experience with Excel, Power Query, data cleaning, visualization, and dashboard design.

Rather than just following tutorials, I wanted to work through a larger dataset, make my own calls on how the data should be analyzed, troubleshoot the problems that came up, and end up with something I could actually put in a portfolio.

It's part of my ongoing journey toward becoming a Data Analyst.

- **GitHub:** [mayur-barase](https://github.com/mayurbarase)
- **LinkedIn:** [Mayur-Barase](https://www.linkedin.com/in/mayur-barase-2b5562364?utm_source=share_via&utm_content=profile&utm_medium=member_android)

---

**Status:** Completed ✅

⭐ If you find this project useful or interesting, feel free to explore the workbook and the analysis!

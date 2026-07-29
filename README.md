# SULAM — RSC Slowbar Street Cafe Data Analytics
### STTHK2113 Data Analytics (B) | Group Assignment 1 | Universiti Utara Malaysia (UUM)

A data analytics and Power BI dashboard project built under the SULAM (community-linked coursework) initiative, analysing real transactional data from
**Rawkstah Coffee (RSC) Slowbar Street Cafe** a student-based café at Inasis Bank Islam, UUM, to generate business insights for the café's owners.

**Group members:**
Siti Ain Athiqah Binti Sahrun (297545) · Hana Syakirah Binti Hassan Khairullah (299403)

**Course:** STTHK2113 Data Analytics (B), School of Computing, UUM (Session 2024/2025, A242)
**Submitted to:** Ts. Dr. Mohamed Ali B. Saip
**Submission date:** 19 June 2025

🔗 **Public Dashboard Link:** https://app.powerbi.com/view?r=eyJrIjoiY2Q2ZDIwYjctMmFmMi00NWQwLWE5YTMtNDdlYTlhZDQwMmRjIiwidCI6ImQ0OTRlMTEzLTUyOGUtNDBhYi05MGQ5LTE2MmRlMmZjYTNmMyIsImMiOjEwfQ%3D%3D

---

## Overview

RSC Slowbar Street Cafe began operating in October 2024, selling Coffee, Non-Coffee, Cream Series, Foods, and Add-ons. Real point-of-sale data was collected directly from the café owners (cumulative sales from 18/10/2024 to 20/05/2025) and analysed to uncover sales trends, product performance, and time-based demand patterns, translated into practical recommendations the owners can act on.

**Headline findings:**
- Total net sales across the collection period: **RM28.78K**, from **2,825 customers**
- Sales are closely tied to the academic calendar — peaks in December, April; a sharp
  dip in February (finals week, students return home)
- **Ice Chocolate** is the overall best-selling product; **Spanish Latte** leads the
  Coffee category specifically
- Customer spending is right-skewed: average spend (RM17.25) sits well above the
  most common spend (RM7.50), driven by a handful of high-value orders
- Strong product association: customers who buy a **Flavour Pump** are ~6x more
  likely to also buy an **Americano**
- **Card/QR payments dominate** (4,493 transactions) over cash (482 transactions)
- Sales cluster by time of day — evenings (6–10 PM) consistently outperform early
  morning hours

## Repository Contents

| File | Description |
|---|---|
| `DatasetOriginal.csv` | Raw point-of-sale export received from the café owner |
| `sulamCode.ipynb` | Jupyter Notebook — data cleaning, transformation, descriptive statistics, association rule mining, and clustering |
| `CleanedDataset.xlsx` | Cleaned & transformed dataset (irrelevant columns dropped, Date/Time split, Product/Category columns derived) |
| `Top_Association_Rules.xlsx` | Output of market basket analysis (product association rules) |
| `sulam_RSC.pbix` | Power BI dashboard file — client-facing visualisations |
| `STTHK2113_REPORT_ASG1.pdf` | Full assignment report — data collection documentation, preprocessing steps, descriptive analytics, insights, and recommendations |

## Methodology

1. **Data collection** — Owner approached directly (via Instagram, then in person);
   raw POS export covering 18/10/2024–20/05/2025 received with owner consent.
2. **Data cleaning (Python/pandas)** — Missing values audited; irrelevant columns
   (`Customer name`, `Customer contacts`, `Cashier name`, `Status`, `POS`, `Store`,
   `Receipt number`, `Taxes`) dropped; rows with missing values removed.
3. **Data transformation** — Combined `Date` column split into separate `Date` and
   `Time` fields; the `Description` field (e.g. *"2 x Hot Americano, 1 x Kaya"*) parsed
   into structured `Product`, `Quantity`, and `Category` columns (Coffee, Non-coffee,
   Food, Add-on, Coffee Beans), with `Hot`/`Ice` prefixes normalised.
4. **Descriptive & inferential analysis (Python)** — Monthly descriptive statistics
   (mean, median, mode, std dev, IQR) for net sales; product association rule mining
   (support/confidence/lift); k-means-style clustering of average net sales by
   operating hour.
5. **Dashboard build (Power BI)** — Client-facing dashboard combining net sales
   trends, gross profit vs. gross sales, top products, time-slot breakdowns, category
   share, and payment method split — filterable by year, time period, month, and
   category.

## Dashboard Contents

- Average / most common customer spend, total net sales, total customers
- Net sales trend by month and year
- Gross profit vs. gross sales by month
- Top 10 most ordered products overall and by AM/PM time slot
- Best-seller product per category
- Sum of quantity sold by category
- Top product association rules (basket analysis)
- Payment type breakdown (card vs. cash)

## Key Recommendations

- **Product & stock:** keep Ice Chocolate consistently stocked; bundle it with
  complementary items; place Flavour Pumps near Americano/coffee prep stations to
  capture the strong co-purchase pattern
- **Time-based promotions:** morning combo deals pairing energising items (Ice
  Chocolate + Kaya Toast); evening upsizing/bundle promos for Spanish Latte and
  16oz cups, since PM traffic is heavier and more exploratory
- **Payments:** keep QR/card payment terminals fast and reliable, since it's the
  clearly preferred method
- **Customer retention:** introduce loyalty programmes or personalised outreach to
  retain the existing ~2,825-customer base, and set concrete growth targets

## Limitations

- May 2025 data is incomplete (dataset cut off mid-month), which may understate
  that month's true performance
- Some descriptive statistics rely on small sample sizes in low-activity months
  (e.g. February 2025, finals week), reducing their reliability
- Clustering and association-rule analysis were exploratory (Python-only) and not
  all findings were carried into the client-facing Power BI dashboard
- Insights are based purely on transactional data; no qualitative customer feedback
  was collected

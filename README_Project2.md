# E-Commerce Revenue, Profitability & Return Rate Analysis (SQL & Python)

![Status](https://img.shields.io/badge/Status-Completed-brightgreen)
![Tools](https://img.shields.io/badge/Tools-SQL%20%7C%20Python%20(Pandas)-blue)
![Focus](https://img.shields.io/badge/Focus-Descriptive%20%26%20Diagnostic%20Analytics-orange)

## 1. Business Problem & Objectives
E-commerce merchants often focus on top-line gross merchandise value (GMV) while overlooking margin erosion from heavy discounting and failed Cash-on-Delivery (COD) returns. This case study analyzes **150 e-commerce transactions** across major Philippine regions to answer three core business questions:
1. **Regional Demand:** Which geographic regions generate the highest realized net revenue and average order value?
2. **Category Profitability:** Which product categories deliver the strongest net profit margins after promotional discounts?
3. **Return Diagnostics:** How strongly do payment methods (COD vs. E-Wallets) and product categories drive order return rates?

---

## 2. Repository Structure
```text
ecommerce-sql-python-analysis/
├── ecommerce_orders_ph.csv          # Cleaned 150-row transactional e-commerce dataset
├── ecommerce_analysis_queries.sql   # Production SQL queries (CTEs, Window Functions, CASE aggregations)
├── ecommerce_eda_analysis.py        # Python Pandas exploratory data analysis & KPI validation script
└── README_Project2.md               # Case study documentation & strategic recommendations
```

---

## 3. Data Dictionary (`ecommerce_orders_ph.csv`)
| Column | Data Type | Description |
| :--- | :--- | :--- |
| `order_id` | String | Unique transaction identifier (`ORD-2026001` to `ORD-2026150`) |
| `order_date` | Date | Transaction date (`YYYY-MM-DD`, Aug–Oct 2026) |
| `customer_id` | String | Unique customer account ID (`CUST-1001` to `CUST-1084`) |
| `region` | String | Philippine delivery region (`Metro Manila`, `Calabarzon`, `Central Luzon`, `Central Visayas`, `Davao Region`) |
| `product_category` | String | Product line (`Electronics`, `Home & Living`, `Fashion & Apparel`, `Health & Beauty`, `Sports & Outdoors`) |
| `sales_channel` | String | Acquisition source (`Shopee/Lazada Marketplace`, `Direct Website`, `Social Commerce (TikTok/FB)`) |
| `payment_method` | String | Checkout method (`E-Wallet (GCash/Maya)`, `Cash on Delivery (COD)`, `Credit/Debit Card`) |
| `quantity` | Integer | Units purchased per order (`1` to `4`) |
| `unit_price_php` | Float | Base item price in Philippine Pesos (₱) |
| `discount_pct` | Float | Promotional discount rate applied (`0.00` to `0.20`) |
| `net_revenue_php` | Float | Post-discount order revenue in PHP (`unit_price_php * quantity * (1 - discount_pct)`) |
| `gross_profit_php` | Float | Net profit after Cost of Goods Sold (`net_revenue_php - COGS`) |
| `order_status` | String | Fulfillment outcome (`Delivered` or `Returned`) |

---

## 4. Key Analytical Findings
* **Realized Revenue & Profit:** Across 150 orders, completed deliveries generated **₱521,064.57** in realized net revenue and **₱122,102.38** in gross profit, with an overall return rate of **7.3%**.
* **Top Performing Region:** **Metro Manila** led all regions in completed order revenue (**₱184,698.88**), followed closely by **Calabarzon**.
* **Margin vs. Volume:** While high-ticket electronics drive substantial top-line revenue, **Sports & Outdoors** generated the highest total gross profit (**₱34,744.03**) due to healthier unit margins and lower discount erosion.
* **Payment Method & Return Risk:** **Cash on Delivery (COD)** orders experienced a **10.4%** return rate compared to **5.7%** for **E-Wallet (GCash/Maya)** transactions—confirming that prepaid digital checkouts significantly reduce failed deliveries.

---

## 5. Strategic Recommendations
1. **Incentivize Prepaid E-Wallet Checkouts:** Offer a ₱50 shipping voucher or 3% instant rebate on **GCash/Maya** orders to shift high-risk COD buyers toward prepaid checkout and cut return losses.
2. **Cap Discounts on High-Margin Categories:** Restrict blanket 15%–20% promo codes on high-demand **Health & Beauty** and **Home & Living** SKUs, reserving deeper discounts for bundle clearance.
3. **Prioritize Calabarzon & Metro Manila Fulfillment:** Pre-allocate fast-moving inventory to regional hubs serving **Metro Manila** and **Calabarzon** to maintain 1–2 day delivery SLAs.

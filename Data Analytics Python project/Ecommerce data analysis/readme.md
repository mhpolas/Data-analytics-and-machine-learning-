#  E‑Commerce — Exploratory Data Analysis (EDA)

A reproducible, end‑to‑end EDA of the public **Brazilian Olist e‑commerce dataset**. The notebook cleans, merges, and analyzes customer, order, product, seller, payment, review, and (optional) geolocation data to answer practical business questions.

> **Deliverable:** `brazilian-olist-e-commerce-dataset-eda.ipynb`
> **Grain:** Item‑level by default (one row per order item). Order‑level metrics are computed with safeguards to avoid double counting.

---

## 🔎 What this project answers

* **Customers**

  * Top cities/states by customers (Q6)
  * Returning vs one‑time customers; counts & chart (Q15)
* **Products & Categories**

  * Category with most items sold (Q8)
  * Products with the longest delivery times (Q19)
  * Categories with highest returns (cancellations) or low ratings (Q22)
* **Orders & Sales**

  * Average Order Value (AOV) (Q9)
  * Orders per month/year (Q23)
  * Seasonality in order volume (Q24)
* **Payments**

  * Average # of installments (Q14)
  * Distribution of installments with % labels on bars
* **Logistics & Reviews**

  * Average purchase→delivery time (Q13)
  * Distribution of review scores (full and by customer averages) (Q16)
  * Late delivery rate and delay breakdowns (optional)

> The notebook includes code snippets for robust counting (e.g., `.nunique()` for `order_id`, `customer_unique_id`) and safe time calculations using `pd.to_datetime` / `pd.to_timedelta`.



## 🧱 Data model & join logic (summary)

* **Core fact:** `order_items` (item‑level)
* **Joins**

  * `orders` → on `order_id`
  * `customers` → on `customer_id` (from `orders`)
  * `products` → on `product_id`
  * `sellers` → on `seller_id`
  * `payments` → aggregate to order‑level first (sum of `payment_value`, max of `payment_sequential`), then join on `order_id`
  * `reviews` → on `order_id`
  * `category translation` → on `product_category_name`
  * *(optional)* `geolocation` → de‑duplicated by `geolocation_zip_code_prefix` before joining to zip prefixes

> **Important:** Because the base is **item‑level**, always use `.nunique()` for counts of `order_id` and `customer_unique_id` to avoid double‑counting.

---

## 📊 Key visuals included

* **Top cities** by unique customers (bar chart)
* **Category with most items sold** (bar chart)
* **AOV**: `payment_value` aggregated **per order**, then averaged
* **Installments distribution** with **percentage labels** (bar chart)
* **Review score distribution** (bar chart)
* **Average delivery time** (summary + optional histogram)
* **Monthly orders** & **seasonality line plot** (trend over time)
* **Slowest products** by average delivery time (table or bar chart)
* **Categories with highest cancellations** and **lowest ratings** (tables)

Each visual has inline explanations and concise interpretation notes.

---

## ✅ Reproducibility & data quality checks

* Type safety for dates: `pd.to_datetime(..., errors='coerce')`
* Time deltas via `pd.to_timedelta` (purchase→approved→delivered)
* Missingness scan per table (print only columns with NAs)
* Grain checks:

  * `order_id`: `nunique()` vs `count()`
  * Item‑level vs order‑level aggregations are kept explicit

---

## 🧠 Notable takeaways (template)

> These will vary with the full dataset. Replace the bullets below with your actual findings after running the notebook on the complete data.

* **AOV:** \~… (currency‑agnostic)
* **Delivery:** Avg purchase→delivery ≈ … days; late delivery rate ≈ …%
* **Seasonality:** Peaks in …; dips in …
* **Categories:** Top sellers by volume: …; categories with low ratings or high cancellations: …
* **Customers:** Returning customers: …% of base; top cities: …

---

## 📝 How to extend

* Add **cohort analysis** (first purchase month → retention by cohort\_index)
* Compute **freight share** (`freight_value / price`) and analyze by category/seller
* Overlay **delay vs review score** relationship (scatter/boxplot)
* Build a small **dashboard** (Power BI / Tableau / Plotly Dash) using the aggregated tables

---

## ⚖️ License

MIT — feel free to use, modify, and distribute with attribution.

---

## 🙌 Acknowledgments

This analysis is based on the public **Olist** e‑commerce dataset. Thanks to the community for maintaining and discussing this benchmark dataset.

---

## 📫 Contact

If you have questions or suggestions, please open an issue or reach out via GitHub.

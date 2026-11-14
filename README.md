# Olist E-Commerce Power BI Analytics
...
<img width="1172" height="677" alt="Overview" src="https://github.com/user-attachments/assets/e9f4e542-67ca-4dd9-a300-80b2491409dc" />
<img width="1162" height="682" alt="Customer analysis" src="https://github.com/user-attachments/assets/2e339471-5981-48ae-af54-f0323d98a882" />
<img width="1167" height="732" alt="Product Highlights" src="https://github.com/user-attachments/assets/60d25502-bea4-485b-8d9f-9a15ec67d9c7" />
<img width="1202" height="687" alt="Sellers Pef" src="https://github.com/user-attachments/assets/5e6aa43b-4d6e-4768-b4a6-d1e3a4aa8e27" />

...
## 📌 Project Overview
An end-to-end Power BI analytics solution for Olist, the Brazilian e-commerce giant. This project transforms raw CSV datasets into an interactive, multi-page dashboard focusing on sales performance, customer behavior, product highlights, and seller logistics.

## 🗄️ Data Architecture & ETL (Power Query)
The raw data consists of 9 distinct CSV files. Extensive ETL processes were applied using Power Query (M) to ensure data quality and clean UI presentation:
* **Encoding & Parsing:** Handled UTF-8 (`65001`) and Western European (`1252`) encodings to preserve Portuguese characters.
* **Type Casting:** Converted string dates to `datetime` objects, keys to `text`, and metrics to `Int64` or `number`.
* **String Formatting:** Applied `Text.Proper` (Capitalize Each Word) to categorical fields (`customer_city`, `seller_city`, `product_category_name_english`, `payment_type`) to remove raw database lowercase formatting.
* **Translation:** Merged and mapped native Portuguese product categories to English (`la_cuisine` -> `Kitchen`).
* **Custom Columns:** Created helper columns like `Installment Plan`, `Installment Sort`, `Short Seller ID`, `Customer Location`, and `Price Group` to optimize front-end visuals.

## 📐 Data Model & Schema
The data model follows a robust, optimized schema designed for bi-directional filtering and accurate cross-highlighting:
* **Fact Tables:** `olist_orders_dataset` and `olist_order_items_dataset` serve as the core fact tables.
* **Dimension Tables:** Connected via 1-to-Many relationships:
  * `Dim_Date` (Custom Date Table for Time Intelligence)
  * `olist_customers_dataset`
  * `olist_sellers_dataset`
  * `olist_products_dataset` (linked to `product_category_name_translation`)
  * `olist_order_payments_dataset`
  * `olist_order_reviews_dataset`
  * `olist_geolocation_dataset`

## 📊 Key DAX Measures
Over 20 custom DAX measures were engineered to drive the KPIs and dashboard visuals:

**Sales & Revenue:**
* `Total Sales`, `Item Sales`, `Avg item price`, `Average Order Purchase`
* `Number of product Sold`, `Orders`

**Customer Insights:**
* `Number of customers`, `Average Customer spend`
* `Repeat Customer Rate`, `AVg number of orders per cst`
* `AVG Review`

**Logistics & Supply Chain:**
* `Average Delivery Time (Days)`, `Delivery Rate`, `Late Delivery %`
* `AVG Freight`, `AVG Freight Cost`, `Freight Cost`, `Freight to Price Ratio`
* `Number of Sellers`

## 🖥️ Dashboard Structure
1. **Overview:** High-level executive KPIs, monthly sales trends, delivery success rates, and top cities by volume.
2. **Customer Analysis:** Geospatial customer distribution, order value grouping, and installment behavior.
3. **Products Highlights:** Category-level performance, price-to-review correlation, and freight burden auditing.
4. **Sellers Performance:** Operational health audit, late delivery tracking by state, and global delivery time distribution.

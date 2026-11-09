# E-Commerce SQL Data Analysis — Task 3

## Project overview
This project demonstrates SQL for data analysis using **SQLite** and a synthetic e-commerce dataset. It was prepared to cover the concepts listed in the Elevate Labs Task 3 brief.

## Dataset
The `dataset/` folder contains five CSV tables:
| Table | Rows | Purpose |
|---|---:|---|
| customers | 80 | Customer profile and city |
| products | 25 | Product catalog and category |
| orders | 220 | Order date and status |
| order_items | 536 | Products, quantities, and prices per order |
| payments | 199 | Payment method, amount, and status |

All records are fictional and created for learning. They do not represent real customers or transactions.

## Relationships
- `orders.customer_id` → `customers.customer_id`
- `order_items.order_id` → `orders.order_id`
- `order_items.product_id` → `products.product_id`
- `payments.order_id` → `orders.order_id`

Some customers have no orders and some orders have no payment record, which makes LEFT JOIN examples meaningful.

## Files
- `Task_3_Ecommerce_SQL_Complete.ipynb` — end-to-end runnable notebook.
- `ecommerce.db` — prebuilt SQLite database.
- `sql/ecommerce_analysis.sql` — standalone SQL queries.
- `dataset/` — source CSVs and dataset notes.
- `outputs/` — CSV exports of selected query results.
- `screenshots/` — rendered query-output tables.
- `Interview_Questions.md` — answers to all seven questions in the task brief.

## Run in Google Colab
1. Upload `Task_3_Ecommerce_SQL_Complete.ipynb` to Google Colab.
2. Run cells from top to bottom.
3. When prompted, upload `Ecommerce_SQL_Practice_Dataset.zip`.
4. The notebook extracts the CSVs, creates the SQLite database, runs data checks and analysis, and exports outputs.

Alternatively, download `ecommerce.db` and open it with DB Browser for SQLite or Python's `sqlite3` module.

## SQL topics covered
`SELECT`, `WHERE`, `ORDER BY`, `GROUP BY`, `HAVING`, `INNER JOIN`, `LEFT JOIN`, subqueries/CTEs, `SUM`, `AVG`, `COUNT`, `COALESCE`, views, indexes, and `EXPLAIN QUERY PLAN`.

## Notes
- SQLite does not support `RIGHT JOIN` in older versions; the equivalent result can be produced by reversing the tables and using `LEFT JOIN`. Recent SQLite versions support RIGHT JOIN.
- Indexes can help larger datasets; on this small practice dataset the query planner may choose a table scan.
- Revenue calculations use `quantity * unit_price` from `order_items`. The example gross revenue includes all order statuses unless a query explicitly filters them.

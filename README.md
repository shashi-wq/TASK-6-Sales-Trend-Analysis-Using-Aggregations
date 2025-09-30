# TASK-6-Sales-Trend-Analysis-Using-Aggregations
## Objective
Analyze monthly revenue and order volume using SQL aggregations.

## Tools
- Google Colab
- SQLite (via Python `sqlite3`)
- Pandas, Matplotlib

## Steps
1. Created `orders` table with `order_id`, `order_date`, `amount`, `product_id`.
2. Used SQL aggregations:
   - `SUM(amount)` for revenue
   - `COUNT(DISTINCT order_id)` for order volume
   - `EXTRACT(YEAR/MONTH)` (or `strftime`) for grouping
3. Visualized monthly revenue and order volume trends.
4. Identified top 3 months by sales.

## SQL Queries
```sql
SELECT 
    strftime('%Y', order_date) AS year,
    strftime('%m', order_date) AS month,
    SUM(amount) AS total_revenue,
    COUNT(DISTINCT order_id) AS order_volume
FROM orders
GROUP BY year, month
ORDER BY year, month;

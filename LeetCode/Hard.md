### Leetcode Problems -> Difficulty = Hard
1479: [Sales by Day of the Week](https://leetcode.com/problems/sales-by-day-of-the-week/)

```sql
SELECT item_category AS CATEGORY,
       Sum(CASE
             WHEN Dayofweek(o.order_date) = 2 THEN quantity
             ELSE 0
           END)      AS MONDAY,
       Sum(CASE
             WHEN Dayofweek(o.order_date) = 3 THEN quantity
             ELSE 0
           END)      AS TUESDAY,
       Sum(CASE
             WHEN Dayofweek(o.order_date) = 4 THEN quantity
             ELSE 0
           END)      AS WEDNESDAY,
       Sum(CASE
             WHEN Dayofweek(o.order_date) = 5 THEN quantity
             ELSE 0
           END)      AS THURSDAY,
       Sum(CASE
             WHEN Dayofweek(o.order_date) = 6 THEN quantity
             ELSE 0
           END)      AS FRIDAY,
       Sum(CASE
             WHEN Dayofweek(o.order_date) = 7 THEN quantity
             ELSE 0
           END)      AS SATURDAY,
       Sum(CASE
             WHEN Dayofweek(o.order_date) = 1 THEN quantity
             ELSE 0
           END)      AS SUNDAY
FROM   items b
       LEFT JOIN orders o using(item_id)
GROUP  BY 1
ORDER  BY 1;

```
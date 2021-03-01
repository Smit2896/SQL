### Leetcode Problems -> Difficulty = Easy

1777: [Product's Price for Each Store](https://leetcode.com/problems/products-price-for-each-store/)

```sql
SELECT product_id,
       Max(CASE
             WHEN store = 'store1' THEN price
           END) AS store1,
       Max(CASE
             WHEN store = 'store2' THEN price
           END) AS store2,
       Max(CASE
             WHEN store = 'store3' THEN price
           END) AS store3
FROM   products
GROUP  BY product_id; 
```

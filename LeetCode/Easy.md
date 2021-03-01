### Leetcode Problems -> Difficulty = Easy

1777: [Product's Price for Each Store](https://leetcode.com/problems/products-price-for-each-store/)

```SQL
SELECT product_id,
    MAX(CASE WHEN store = 'store1' THEN price END) as store1,
    MAX(CASE WHEN store = 'store2' THEN price END) as store2,
    MAX(CASE WHEN store = 'store3' THEN price END) as store3
FROM Products
GROUP BY product_id;
```
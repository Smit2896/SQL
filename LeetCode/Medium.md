### Leetcode Problems -> Difficulty = Medium

1421: [NPV Queries](https://leetcode.com/problems/npv-queries/)

```sql
SELECT q.id,
       q.year,
       COALESCE(n.npv, 0) AS npv
FROM   queries q
       LEFT JOIN npv n using(id, year)
ORDER  BY 1,
          2; 
```
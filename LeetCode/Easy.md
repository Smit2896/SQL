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
1280: [Students and Examinations](https://leetcode.com/problems/students-and-examinations/)

~~~sql
SELECT s.student_id,
       s.student_name,
       sub.subject_name,
       Count(e.subject_name) AS attended_exams
FROM   students s
       CROSS JOIN subjects sub
       LEFT JOIN examinations e using(student_id, subject_name)
GROUP  BY s.student_id,
          sub.subject_name
ORDER  BY s.student_id,
          sub.subject_name

~~~
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
# Transpose
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
#Challenging
~~~
1517: [Find Users With Valid E-Mails](https://leetcode.com/problems/find-users-with-valid-e-mails/)

```sql
SELECT *
FROM   users
WHERE  mail REGEXP '^[a-zA-Z][a-zA-Z0-9\.\_\-]*@leetcode.com$'

#RegexEmailQuery - Challenging
```
1623: [All Valid Triplets That Can Represent a Country](https://leetcode.com/problems/all-valid-triplets-that-can-represent-a-country/)

```sql
SELECT A.student_name AS member_A,
       B.student_name AS member_B,
       C.student_name AS member_C
FROM   schoola A,
       schoolb B,
       schoolc C
WHERE  ( A.student_name != B.student_name
         AND C.student_name != B.student_name
         AND A.student_name != C.student_name )
       AND ( A.student_id != B.student_id
             AND C.student_id != B.student_id
             AND A.student_id != C.student_id ) 
#Tricky conditions    
```

1633: [Percentage of Users Attended a Contest](https://leetcode.com/problems/percentage-of-users-attended-a-contest/)

```sql
SELECT r.contest_id,
       Round((Count(r.user_id) / (SELECT Count(*)
                                   FROM   users) ) * 100, 2) AS percentage
FROM   register r
       JOIN users u using(user_id)
GROUP  BY r.contest_id
ORDER  BY percentage DESC,
          r.contest_id 
```
1241: [Number of Comments per Post](https://leetcode.com/problems/number-of-comments-per-post/)

```sql
SELECT A.sub_id                 AS post_id,
       Count(DISTINCT B.sub_id) AS number_of_comments
FROM   submissions A
       LEFT JOIN submissions B
              ON A.sub_id = B.parent_id
WHERE  A.parent_id IS NULL
GROUP  BY A.sub_id 
##For me - self join queries are little tricky
```

1527: [Patients With a Condition](https://leetcode.com/problems/patients-with-a-condition/)

```sql
SELECT *
FROM   patients
WHERE  conditions LIKE 'DIAB1%'
        OR conditions LIKE '% DIAB1%' 
#very simple - though one might forget the second condition here
```
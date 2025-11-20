# 1068. Product Sales Analysis I

**Difficulty:** Easy  
**Topics:** `LEFT JOIN`  
**LeedCode Link:** https://leetcode.com/problems/product-sales-analysis-i/

## ❓ Problem Statement
Write a solution to report the `product_name`, `year`, and `price` for each `sale_id` in the `Sales` table.	
Return the resulting table in any order.

## 🗂️ Table Schema
Table: ```Sales```
```sql

+-------------+-------+
| Column Name | Type  |
+-------------+-------+
| sale_id     | int   |
| product_id  | int   |
| year        | int   |
| quantity    | int   |
| price       | int   |
+-------------+-------+
(sale_id, year) is the primary key.
product_id is a foreign key to Product table.
Note that the price is per unit.

```

Table: ```Product```
```sql
+--------------+---------+
| Column Name  | Type    |
+--------------+---------+
| product_id   | int     |
| product_name | varchar |
+--------------+---------+
product_id is the primary key.
```
## 💡 Solution
```sql
SELECT
  product_name,
  year,
  price
FROM
  Sales AS s
LEFT JOIN
  Product AS p
ON
  s.product_id = p.product_id;
```

# 595. Big Countries

**Difficulty:** Easy  
**Topics:** `Conditional Filtering`, `WHERE Clause`, `OR Operator`, `Comparative Operators`  
**LeedCode Link:** https://leetcode.com/problems/big-countries/

## ❓ Problem Statement
A country is big if:
1. it has an area of at least three million (i.e., 3000000 km2), or
2. it has a population of at least twenty-five million (i.e., 25000000).

Write a solution to find the name, population, and area of the big countries.

Return the result table in any order.

## 🗂️ Table Schema
Table: ```World```
```sql

+-------------+---------+
| Column Name | Type    |
+-------------+---------+
| name        | varchar |
| continent   | varchar |
| area        | int     |
| population  | int     |
| gdp         | bigint  |
+-------------+---------+

name is the primary key.
```

## 💡 Solution
```sql
SELECT
  name,
  population,
  area
FROM
  World
WHERE
  area >= 3000000
  OR population >= 25000000;
```

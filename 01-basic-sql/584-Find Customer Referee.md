# 584. Find Customer Referee

**Difficulty:** Easy  
**Topics:** `Basic Filtering`, `WHERE Clause`, `OR`, `OR Operator`, `Inequality Conditions`  
**LeedCode Link:** https://leetcode.com/problems/recyclable-and-low-fat-products/

## ❓ Problem Statement
Find the names of the customer that are either:
1. referred by any customer with id != 2.
2. not referred by any customer.
Return the result table in any order.

## 🗂️ Table Schema
Table: ```Customer```
```sql

+-------------+---------+
| Column Name | Type    |
+-------------+---------+
| id          | int     |
| name        | varchar |
| referee_id  | int     |
+-------------+---------+


id is the primary key.  
```

## 💡 Solution
```sql
SELECT
  name
FROM
  Customer
WHERE
  referee_id IS NULL
  OR referee_id != 2;
```

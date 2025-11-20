# 1378. Replace Employee ID With The Unique Identifier

**Difficulty:** Easy  
**Topics:** `LEFT JOIN`  
**LeedCode Link:** https://leetcode.com/problems/replace-employee-id-with-the-unique-identifier/

## ❓ Problem Statement
Write a solution to show the unique ID of each user, If a user does not have a unique ID replace just show `null`.	
Return the result table in any order.

## 🗂️ Table Schema
Table: ```Employees```
```sql

+---------------+---------+
| Column Name   | Type    |
+---------------+---------+
| id            | int     |
| name          | varchar |
+---------------+---------+
id is the primary key.

```

Table: ```EmployeeUNI```
```sql
+---------------+---------+
| Column Name   | Type    |
+---------------+---------+
| id            | int     |
| unique_id     | int     |
+---------------+---------+
(id, unique_id) is the primary key.
```
## 💡 Solution
```sql
SELECT
  eu.unique_id AS unique_id,
  e.name AS name
FROM
  Employees AS e
LEFT JOIN
  EmployeeUNI AS eu
ON
  e.id = eu.id;
```

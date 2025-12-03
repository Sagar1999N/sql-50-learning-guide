# 197. Rising Temperature

**Difficulty:** Easy  
**Topics:** `Date Functions`, `Self-Join`, `Comparative Analysis`, `Subqueries`/`JOIN`  
**LeedCode Link:** https://leetcode.com/problems/rising-temperature/

## ❓ Problem Statement
Write a solution to find all dates' id with higher temperatures compared to its previous dates (yesterday).	
Return the result table in any order.


## 🗂️ Table Schema
Table: ```Weather```
```sql

+---------------+---------+
| Column Name   | Type    |
+---------------+---------+
| id            | int     |
| recordDate    | date    |
| temperature   | int     |
+---------------+---------+
id is the column with unique values for this table.
There are no different rows with the same recordDate.
This table contains information about the temperature on a certain day.
```

## 💡 Solution
```sql
-- Using JOIN
SELECT
  a.id AS Id
FROM
  Weather a
JOIN
  Weather b
ON
  a.recordDate = DATE_ADD(b.recordDate, INTERVAL 1 DAY)
  WHERE a.temperature > b.temperature;
```

## 🔄 Alternative Approach
```sql
-- Using Subquery
SELECT
  b.id AS Id
FROM
  Weather b
WHERE
  b.temperature > (
  SELECT
    a.temperature
  FROM
    Weather a
  WHERE
    DATEDIFF(b.recordDate,
      a.recordDate) = 1);
```


# 1581. Customer Who Visited but Did Not Make Any Transactions

**Difficulty:** Easy  
**Topics:** `GROUP BY`, `COUNT`, (`NOT IN`, `Subqueries`)/`LEFT JOIN`
**LeedCode Link:** https://leetcode.com/problems/customer-who-visited-but-did-not-make-any-transactions/

## ❓ Problem Statement
Write a solution to find the IDs of the users who visited without making any transactions and the number of times they made these types of visits.	
Return the result table sorted in any order.

## 🗂️ Table Schema
Table: ```Visits```
```sql

+-------------+---------+
| Column Name | Type    |
+-------------+---------+
| visit_id    | int     |
| customer_id | int     |
+-------------+---------+
visit_id is the column with unique values for this table.
This table contains information about the customers who visited the mall.
```

Table: ```Transactions```
```sql

+----------------+---------+
| Column Name    | Type    |
+----------------+---------+
| transaction_id | int     |
| visit_id       | int     |
| amount         | int     |
+----------------+---------+
transaction_id is column with unique values for this table.
This table contains information about the transactions made during the visit_id.
```
## 💡 Solution
```sql
SELECT
  customer_id,
  COUNT(1) AS count_no_trans
FROM
  Visits
WHERE
  visit_id NOT IN (
  SELECT
    DISTINCT visit_id
  FROM
    Transactions)
GROUP BY
  customer_id;
```

## 🔄 Alternative Approach
```sql
-- Using LEFT JOIN
SELECT
  V.customer_id,
  COUNT(V.visit_id) AS count_no_trans
FROM
  Visits AS V
LEFT JOIN
  Transactions AS T
ON
  V.visit_id = T.visit_id
WHERE
  T.visit_id IS NULL
GROUP BY
  V.customer_id;
```

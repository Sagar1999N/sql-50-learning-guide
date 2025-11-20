# 1148. Article Views I

**Difficulty:** Easy  
**Topics:** `Basic Filtering`, `WHERE Clause`, `ORDER BY`, `DISTINCT Keyword`, `Duplicate Removal`, `Self-Comparison`  
**LeedCode Link:** https://leetcode.com/problems/article-views-i/

## ❓ Problem Statement
Write a solution to find all the authors that viewed at least one of their own articles.
Return the result table sorted by id in ascending order.

## 🗂️ Table Schema
Table: ```Views```
```sql

+---------------+---------+
| Column Name   | Type    |
+---------------+---------+
| article_id    | int     |
| author_id     | int     |
| viewer_id     | int     |
| view_date     | date    |
+---------------+---------+

There is no primary key.
The table may have duplicate rows.
Table indicates that some viewer viewed an article (written by some author) on some date. 
Note that equal author_id and viewer_id indicate the same person.
```

## 💡 Solution
```sql
SELECT
  DISTINCT(author_id) AS id
FROM
  Views
WHERE
  author_id = viewer_id
ORDER BY
  id;
```

## 🔄 Alternative Approach
```sql
-- Using GROUP BY
SELECT
  author_id AS id
FROM
  Views
WHERE
  author_id = viewer_id
GROUP BY
  author_id
ORDER BY
  id;
```

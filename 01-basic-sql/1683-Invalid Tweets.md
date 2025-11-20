# 1683. Invalid Tweets

**Difficulty:** Easy  
**Topics:** `Basic Filtering`, `WHERE Clause`, `LENGTH Function`  
**LeedCode Link:** https://leetcode.com/problems/invalid-tweets/

## ❓ Problem Statement
Write a solution to find the IDs of the invalid tweets. The tweet is invalid if the number of characters used in the content of the tweet is strictly greater than 15.
Return the result table in any order.

## 🗂️ Table Schema
Table: ```Tweets```
```sql

+----------------+---------+
| Column Name    | Type    |
+----------------+---------+
| tweet_id       | int     |
| content        | varchar |
+----------------+---------+

tweet_id is the primary key.
This table contains all the tweets in a social media app.
```

## 💡 Solution
```sql
SELECT
  tweet_id
FROM
  Tweets
WHERE
  LENGTH(content) > 15;
```

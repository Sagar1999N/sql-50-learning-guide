# 1757. Recyclable and Low Fat Products

**Difficulty:** Easy  
**LeedCode Link:** https://leetcode.com/problems/recyclable-and-low-fat-products/

## ❓ Problem Statement
Write a solution to find the ids of products that are both low fat and recyclable.
Return the result table in any order.

## 💡 Solution
```sql
SELECT
  product_id
FROM
  Products
WHERE
  low_fats = "Y"
  AND recyclable = "Y";
```

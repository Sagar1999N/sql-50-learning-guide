# 1757. Recyclable and Low Fat Products

**Difficulty:** Easy  
**Topics:** `Basic Filtering`, `WHERE Clause`  
**LeedCode Link:** https://leetcode.com/problems/recyclable-and-low-fat-products/

## ❓ Problem Statement
Write a solution to find the ids of products that are both low fat and recyclable.
Return the result table in any order.

## 🗂️ Table Schema
Table: ```Products```
```sql
+-------------+---------+
| Column Name | Type    |
+-------------+---------+
| product_id  | int     |
| low_fats    | enum    |
| recyclable  | enum    |
+-------------+---------+
```
product_id is the primary key.  
low_fats is an ENUM of type ('Y', 'N')  
recyclable is an ENUM of type ('Y', 'N')  

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
## 🧠 Key Learnings  
1. Basic WHERE Clause: Filtering rows based on conditions  
2. AND Operator: Combining multiple conditions (both must be true)  
3. ENUM Handling: Working with categorical data stored as ENUM types  
4. Simple SELECT: Returning only specific columns instead of all columns  

## 🔄 Alternative Approach
```sql
-- Using CASE statements (unnecessarily complex for this problem)
SELECT product_id
FROM Products
WHERE 
  CASE WHEN low_fats = 'Y' THEN 1 ELSE 0 END = 1
  AND CASE WHEN recyclable = 'Y' THEN 1 ELSE 0 END = 1;
```
Note: This demonstrates alternative logic but is not recommended for simple problems.

## ⚡ Performance Notes
- This is the most efficient approach for this problem
- Uses simple filtering without joins or subqueries
- Optimal for large datasets  

## 📚 Related Problems
- Next Step: 584. Find Customer Referee - Similar filtering with different conditions  
- Similar Concept: 595. Big Countries - Multiple OR conditions in WHERE clause

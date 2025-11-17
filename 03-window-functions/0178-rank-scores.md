# 178. Rank Scores

**Topics:** `Window Functions`  
**Difficulty:** Medium  
**LeetCode Link:** https://leetcode.com/problems/rank-scores/

## ❓ Problem Statement
Write a SQL query to rank scores. If there is a tie between two scores, both should have the same ranking. After a tie, the next ranking number should be the next consecutive integer value.

## 💡 Solution
```sql
SELECT 
    score,
    DENSE_RANK() OVER (ORDER BY score DESC) as 'rank'
FROM Scores;
```

## 🧠 Key Learnings
1. **DENSE_RANK() vs RANK()**: DENSE_RANK doesn't skip numbers after ties, while RANK does
2. **Window Function Execution**: Window functions process after WHERE and GROUP BY clauses
3. **ORDER BY in OVER()**: Determines the order for ranking calculation

## 🔄 Alternative Approach
```sql
-- Using correlated subquery
SELECT s1.score, (
    SELECT COUNT(DISTINCT s2.score) 
    FROM Scores s2 
    WHERE s2.score >= s1.score
) as 'rank'
FROM Scores s1
ORDER BY s1.score DESC;
```
**Note:** This approach is less efficient (O(n²) complexity) but helps understand the logic.

## 📚 Related Problems
- **Next in difficulty**: [185. Department Top Three Salaries](0185-department-top-three.md)
- **Similar concept**: [177. Nth Highest Salary](../04-subqueries-ctes/0177-nth-highest-salary.md)

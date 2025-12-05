# 1280. Students and Examinations

**Difficulty:** Easy  
**Topics:** `CROSS JOIN`, `LEFT JOIN`, `Conditional Aggregation`, `Comprehensive Combinations`  
**LeedCode Link:** https://leetcode.com/problems/students-and-examinations/

## ❓ Problem Statement
Write a solution to find the number of times each student attended each exam.
Return the result table ordered by `student_id` and `subject_name`.

## 🗂️ Table Schema
Table: ```Students```
```sql

+---------------+---------+
| Column Name   | Type    |
+---------------+---------+
| student_id    | int     |
| student_name  | varchar |
+---------------+---------+
student_id is the primary key (column with unique values) for this table.
Each row of this table contains the ID and the name of one student in the school.
```

Table: ```Subjects```
```sql

+--------------+---------+
| Column Name  | Type    |
+--------------+---------+
| subject_name | varchar |
+--------------+---------+
subject_name is the primary key (column with unique values) for this table.
Each row of this table contains the name of one subject in the school.
 
```
Table: ```Examinations```
```sql
+--------------+---------+
| Column Name  | Type    |
+--------------+---------+
| student_id   | int     |
| subject_name | varchar |
+--------------+---------+
There is no primary key (column with unique values) for this table. It may contain duplicates.
Each student from the Students table takes every course from the Subjects table.
Each row of this table indicates that a student with ID student_id attended the exam of subject_name.
```

## 💡 Solution
```sql
---Using Sum / Count 
SELECT
  ss.student_id,
  ss.student_name,
  ss.subject_name,
  SUM(CASE
      WHEN e.student_id IS NOT NULL THEN 1
      ELSE 0
  END
    ) AS attended_exams
  -- COUNT(e.subject_name) AS attended_exams
FROM (
  SELECT
    s.student_id,
    s.student_name,
    sj.subject_name
  FROM
    Students s
  CROSS JOIN
    Subjects sj) AS ss
LEFT JOIN
  Examinations AS e
ON
  ss.student_id = e.student_id
  AND ss.subject_name = e.subject_name
GROUP BY
  ss.student_id,
  ss.subject_name
ORDER BY
  ss.student_id,
  ss.subject_name;
```

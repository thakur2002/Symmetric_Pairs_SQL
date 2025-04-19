# ✅ Symmetric Pairs – SQL Solution

**🧩 Problem Name:** [Symmetric Pairs](https://www.hackerrank.com/challenges/symmetric-pairs/problem)  
**📁 Platform:** HackerRank  
**🧠 Difficulty:** Medium  
**📌 Topic:** SQL, Self Joins, Grouping, Filtering

---

## 📄 Problem Description

Given a table `functions(X, Y)`, the task is to find all **symmetric pairs** such that both `(X, Y)` and `(Y, X)` exist in the table.

Special case: if `X = Y`, include the pair only if it occurs **more than once** in the dataset.

---

## ✅ SQL Solution

```sql
SELECT f1.X, f1.Y
FROM functions f1
JOIN functions f2 ON f1.X = f2.Y AND f1.Y = f2.X
WHERE f1.X <= f1.Y
GROUP BY f1.X, f1.Y
HAVING (f1.X = f1.Y AND COUNT(*) > 1) OR f1.X <> f1.Y
ORDER BY f1.X;
```
## Explanation:
Performs a self-join on the functions table to find pairs (X, Y) and their reverse (Y, X).

Ensures no duplicates or mirror duplicates by checking f1.X <= f1.Y.

Uses GROUP BY and HAVING to handle:

Reflexive pairs like (1,1) appearing more than once.

Symmetric distinct pairs like (2,3) and (3,2).

Orders the output by the first column (X) for consistent results.

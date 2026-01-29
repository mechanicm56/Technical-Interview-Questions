# 📘 SQL Interview Cheat Sheet (Basic → Advanced)

This repository contains a **complete SQL interview cheat sheet** covering **basic to advanced SQL concepts** frequently asked in:
- Software interviews
- Backend / Full‑stack roles
- Product companies
- Service‑based companies

---

## 📌 Topics Covered
- Basic SQL queries
- Joins & subqueries
- Aggregations
- Window functions
- CTEs
- Indexing & performance
- Transactions & ACID
- Normalization
- Advanced interview questions

---

## 🔹 1. BASIC SQL

### SELECT
```sql
SELECT col1, col2 FROM table;
```

### WHERE
```sql
SELECT * FROM emp WHERE salary > 50000;
```

### DISTINCT
```sql
SELECT DISTINCT dept FROM emp;
```

### ORDER BY
```sql
SELECT * FROM emp ORDER BY salary DESC;
```

### LIMIT / TOP
```sql
SELECT * FROM emp LIMIT 5;     -- MySQL / PostgreSQL
SELECT TOP 5 * FROM emp;      -- SQL Server
```

---

## 🔹 2. AGGREGATE FUNCTIONS

```sql
COUNT(), SUM(), AVG(), MIN(), MAX()
```

```sql
SELECT dept, COUNT(*) 
FROM emp
GROUP BY dept;
```

---

## 🔹 3. WHERE vs HAVING

| WHERE | HAVING |
|-----|-------|
| Filters rows | Filters groups |
| Before GROUP BY | After GROUP BY |
| No aggregates | Aggregates allowed |

```sql
SELECT dept, COUNT(*) 
FROM emp
GROUP BY dept
HAVING COUNT(*) > 5;
```

---

## 🔹 4. JOINS

### INNER JOIN
```sql
SELECT *
FROM emp e
JOIN dept d ON e.dept_id = d.id;
```

### LEFT JOIN
```sql
SELECT *
FROM emp e
LEFT JOIN dept d ON e.dept_id = d.id;
```

### RIGHT JOIN
```sql
SELECT *
FROM emp e
RIGHT JOIN dept d ON e.dept_id = d.id;
```

### FULL JOIN
```sql
SELECT *
FROM emp e
FULL JOIN dept d ON e.dept_id = d.id;
```

---

## 🔹 5. SUBQUERIES

```sql
SELECT *
FROM emp
WHERE salary > (SELECT AVG(salary) FROM emp);
```

```sql
SELECT *
FROM emp e
WHERE salary >
(SELECT AVG(salary) FROM emp WHERE dept = e.dept);
```

---

## 🔹 6. EXISTS vs IN

```sql
SELECT *
FROM emp e
WHERE EXISTS (
  SELECT 1 FROM dept d WHERE d.id = e.dept_id
);
```

---

## 🔹 7. WINDOW FUNCTIONS

```sql
SELECT *,
RANK() OVER (PARTITION BY dept ORDER BY salary DESC) rnk
FROM emp;
```

---

## 🔹 8. Nth Highest Salary

```sql
SELECT salary
FROM (
  SELECT salary,
  DENSE_RANK() OVER (ORDER BY salary DESC) rnk
  FROM emp
) t
WHERE rnk = 3;
```

---

## 🔹 9. CTE

```sql
WITH high_paid AS (
  SELECT * FROM emp WHERE salary > 70000
)
SELECT * FROM high_paid;
```

---

## 🔹 10. INDEX

```sql
CREATE INDEX idx_salary ON emp(salary);
```

---

## 🔹 11. TRANSACTIONS & ACID

```sql
BEGIN;
UPDATE emp SET salary = 60000 WHERE id = 1;
COMMIT;
ROLLBACK;
```

---

## 🔹 12. DELETE vs TRUNCATE vs DROP

| Command | Rollback | Speed | Structure |
|------|----------|-------|----------|
| DELETE | Yes | Slow | Kept |
| TRUNCATE | No | Fast | Kept |
| DROP | No | Fastest | Removed |

---

## 🔹 13. UNION vs UNION ALL

| UNION | UNION ALL |
|-----|-----------|
| Removes duplicates | Keeps duplicates |

---

## ⚡ QUICK RULES

- WHERE → rows
- HAVING → groups
- EXISTS faster than IN
- Index speeds read, slows write
- Window functions use OVER()

---

⭐ Perfect for SQL interview revision!

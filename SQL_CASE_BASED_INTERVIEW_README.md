# 📘 Case-Based SQL Problems (Product Company Interviews)

This README contains **real-world, case-based SQL problems** commonly asked in **product companies** like Amazon, Google, Uber, Flipkart, Microsoft, etc.
Each problem includes a **clear schema + interview-ready solution**.

---

## 🧩 CASE 1: Second Highest Salary

**Table:** employees(id, name, salary)

```sql
SELECT MAX(salary) AS second_highest_salary
FROM employees
WHERE salary < (SELECT MAX(salary) FROM employees);
```

---

## 🧩 CASE 2: Nth Highest Salary

```sql
SELECT salary
FROM (
  SELECT salary,
         DENSE_RANK() OVER (ORDER BY salary DESC) AS rnk
  FROM employees
) t
WHERE rnk = N;
```

---

## 🧩 CASE 3: Employees Earning More Than Their Manager

**Table:** employees(id, name, salary, manager_id)

```sql
SELECT e.name
FROM employees e
JOIN employees m
ON e.manager_id = m.id
WHERE e.salary > m.salary;
```

---

## 🧩 CASE 4: Customers Who Never Ordered

**Tables:** customers(id, name), orders(id, customer_id)

```sql
SELECT c.name
FROM customers c
LEFT JOIN orders o
ON c.id = o.customer_id
WHERE o.id IS NULL;
```

---

## 🧩 CASE 5: Department With Highest Average Salary

```sql
SELECT dept_id
FROM employees
GROUP BY dept_id
ORDER BY AVG(salary) DESC
LIMIT 1;
```

---

## 🧩 CASE 6: Find Duplicate Records

**Table:** users(id, email)

```sql
SELECT email, COUNT(*) AS cnt
FROM users
GROUP BY email
HAVING COUNT(*) > 1;
```

---

## 🧩 CASE 7: Delete Duplicate Records (Keep One)

```sql
DELETE FROM users
WHERE id NOT IN (
  SELECT MIN(id)
  FROM users
  GROUP BY email
);
```

---

## 🧩 CASE 8: Running Total / Cumulative Sum

**Table:** sales(date, amount)

```sql
SELECT date,
       amount,
       SUM(amount) OVER (ORDER BY date) AS running_total
FROM sales;
```

---

## 🧩 CASE 9: Top 3 Salaries in Each Department

```sql
SELECT *
FROM (
  SELECT name,
         dept_id,
         salary,
         DENSE_RANK() OVER (PARTITION BY dept_id ORDER BY salary DESC) AS rnk
  FROM employees
) t
WHERE rnk <= 3;
```

---

## 🧩 CASE 10: Find Missing IDs

**Table:** numbers(id)

```sql
SELECT n1.id + 1 AS missing_id
FROM numbers n1
LEFT JOIN numbers n2
ON n1.id + 1 = n2.id
WHERE n2.id IS NULL;
```

---

## 🧩 CASE 11: First Record Per Group

```sql
SELECT *
FROM (
  SELECT *,
         ROW_NUMBER() OVER (PARTITION BY dept_id ORDER BY salary DESC) AS rn
  FROM employees
) t
WHERE rn = 1;
```

---

## 🧩 CASE 12: Employees Earning Above Company Average

```sql
SELECT *
FROM employees
WHERE salary > (SELECT AVG(salary) FROM employees);
```

---

## ⚡ PRODUCT COMPANY INTERVIEW TIPS

- Prefer **WINDOW FUNCTIONS**
- Handle **NULL cases**
- Avoid unnecessary subqueries
- Explain **time complexity**
- Use **CTEs** for clean logic

---

## 🧠 ONE-LINE MEMORY TRICKS

- Ranking → `DENSE_RANK()`
- Top-N per group → `PARTITION BY`
- Missing rows → `LEFT JOIN + IS NULL`
- Dedup → `GROUP BY + HAVING`

---

⭐ This single README is enough to clear **most SQL rounds in product companies**.

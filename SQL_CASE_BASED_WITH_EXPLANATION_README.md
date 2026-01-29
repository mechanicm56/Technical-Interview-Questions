# 📘 Case-Based SQL Problems with Detailed Explanations (Product Companies)

This README contains **real-world SQL case-based problems** asked in **product company interviews**  
(Amazon, Google, Uber, Flipkart, Microsoft) with **clear explanations + solutions**.

---

## 🧩 CASE 1: Second Highest Salary

**Table:** employees(id, name, salary)

### ✅ Query
```sql
SELECT MAX(salary)
FROM employees
WHERE salary < (SELECT MAX(salary) FROM employees);
```

### 🧠 Explanation
- Inner query finds the **highest salary**
- Outer query finds the **maximum salary less than the highest**
- Works even if highest salary appears multiple times

---

## 🧩 CASE 2: Nth Highest Salary

### ✅ Query
```sql
SELECT salary
FROM (
  SELECT salary, DENSE_RANK() OVER (ORDER BY salary DESC) rnk
  FROM employees
) t
WHERE rnk = N;
```

### 🧠 Explanation
- `DENSE_RANK()` assigns rank based on salary
- Same salaries get same rank
- Filter on rank = N to get Nth highest

---

## 🧩 CASE 3: Employees Earning More Than Their Manager

**Table:** employees(id, name, salary, manager_id)

### ✅ Query
```sql
SELECT e.name
FROM employees e
JOIN employees m ON e.manager_id = m.id
WHERE e.salary > m.salary;
```

### 🧠 Explanation
- Self join employees table
- Compare employee salary with manager salary
- Return employees earning more than their managers

---

## 🧩 CASE 4: Customers Who Never Ordered

**Tables:** customers(id, name), orders(id, customer_id)

### ✅ Query
```sql
SELECT c.name
FROM customers c
LEFT JOIN orders o ON c.id = o.customer_id
WHERE o.id IS NULL;
```

### 🧠 Explanation
- LEFT JOIN keeps all customers
- NULL in orders means no matching order
- Filter NULLs to find customers with no orders

---

## 🧩 CASE 5: Department With Highest Average Salary

### ✅ Query
```sql
SELECT dept_id
FROM employees
GROUP BY dept_id
ORDER BY AVG(salary) DESC
LIMIT 1;
```

### 🧠 Explanation
- Group employees by department
- Calculate average salary
- Sort descending and take top department

---

## 🧩 CASE 6: Find Duplicate Records

**Table:** users(id, email)

### ✅ Query
```sql
SELECT email, COUNT(*)
FROM users
GROUP BY email
HAVING COUNT(*) > 1;
```

### 🧠 Explanation
- GROUP BY email groups duplicates
- HAVING filters only duplicate emails

---

## 🧩 CASE 7: Delete Duplicate Records (Keep One)

### ✅ Query
```sql
DELETE FROM users
WHERE id NOT IN (
  SELECT MIN(id)
  FROM users
  GROUP BY email
);
```

### 🧠 Explanation
- Keep smallest id per email
- Delete all other duplicate rows

---

## 🧩 CASE 8: Running Total / Cumulative Sum

**Table:** sales(date, amount)

### ✅ Query
```sql
SELECT date, amount,
       SUM(amount) OVER (ORDER BY date) AS running_total
FROM sales;
```

### 🧠 Explanation
- Window function calculates cumulative sum
- ORDER BY date ensures correct sequence

---

## 🧩 CASE 9: Top 3 Salaries in Each Department

### ✅ Query
```sql
SELECT *
FROM (
  SELECT name, dept_id, salary,
         DENSE_RANK() OVER (PARTITION BY dept_id ORDER BY salary DESC) rnk
  FROM employees
) t
WHERE rnk <= 3;
```

### 🧠 Explanation
- Partition by department
- Rank salaries within each department
- Filter top 3

---

## 🧩 CASE 10: Find Missing IDs

**Table:** numbers(id)

### ✅ Query
```sql
SELECT n1.id + 1 AS missing_id
FROM numbers n1
LEFT JOIN numbers n2 ON n1.id + 1 = n2.id
WHERE n2.id IS NULL;
```

### 🧠 Explanation
- Check next expected ID
- If missing in table, it appears as NULL

---

## 🧩 CASE 11: First Record Per Group

### ✅ Query
```sql
SELECT *
FROM (
  SELECT *,
         ROW_NUMBER() OVER (PARTITION BY dept_id ORDER BY salary DESC) rn
  FROM employees
) t
WHERE rn = 1;
```

### 🧠 Explanation
- ROW_NUMBER assigns unique row numbers
- Pick first row per department

---

## 🧩 CASE 12: Employees Earning Above Company Average

### ✅ Query
```sql
SELECT *
FROM employees
WHERE salary > (SELECT AVG(salary) FROM employees);
```

### 🧠 Explanation
- Subquery computes company average
- Outer query filters higher earners

---

## ⚡ PRODUCT COMPANY INTERVIEW TIPS

- Prefer **WINDOW FUNCTIONS**
- Explain logic before query
- Handle **NULLs**
- Avoid correlated subqueries when possible
- Use CTEs for clarity

---

⭐ This README is **interview-ready** for product companies.

# Using the Set Operators - Assignment

## Q1. Create a matrix query to display the job, the salary for that job based on department number, and the total salary for that job, for departments 10, 20, and 30.

```sql
SELECT job,
       SUM(CASE WHEN deptno = 10 THEN sal ELSE 0 END) AS Dept10,
       SUM(CASE WHEN deptno = 20 THEN sal ELSE 0 END) AS Dept20,
       SUM(CASE WHEN deptno = 30 THEN sal ELSE 0 END) AS Dept30,
       SUM(sal) AS Total_Salary
FROM emp
GROUP BY job
ORDER BY job;
```

---

## Q2. Using Set Operator display the DEPTNO, SUM(SAL) for each department, JOB, SUM(SAL) for each job and Total Salary.

```sql
SELECT TO_CHAR(deptno) AS Category,
       SUM(sal) AS Total_Salary
FROM emp
GROUP BY deptno

UNION ALL

SELECT job,
       SUM(sal)
FROM emp
GROUP BY job

UNION ALL

SELECT 'TOTAL',
       SUM(sal)
FROM emp;
```

---

## Q3. Using Set Operator display the JOB and DEPTNO of employees working in department 20, 10 and 30 in that order.

```sql
SELECT job, deptno
FROM emp
WHERE deptno = 20

UNION ALL

SELECT job, deptno
FROM emp
WHERE deptno = 10

UNION ALL

SELECT job, deptno
FROM emp
WHERE deptno = 30;
```

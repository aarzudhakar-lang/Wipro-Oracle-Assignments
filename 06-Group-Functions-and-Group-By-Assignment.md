# Group Functions & GROUP BY Assignment

## Q1. Find the highest, lowest, sum, and average salary of all employees.

```sql
SELECT MAX(sal) AS Maximum,
       MIN(sal) AS Minimum,
       SUM(sal) AS Sum,
       ROUND(AVG(sal), 2) AS Average
FROM emp;
```

## Q2. Round the average salary to the nearest whole number.

```sql
SELECT MAX(sal) AS Maximum,
       MIN(sal) AS Minimum,
       SUM(sal) AS Sum,
       ROUND(AVG(sal)) AS Average
FROM emp;
```

## Q3. Display the minimum, maximum, sum, and average salary for each job type.

```sql
SELECT job,
       MIN(sal) AS Minimum,
       MAX(sal) AS Maximum,
       SUM(sal) AS Sum,
       ROUND(AVG(sal)) AS Average
FROM emp
GROUP BY job;
```

## Q4. Display the number of people with the same job.

```sql
SELECT job,
       COUNT(*) AS Number_of_Employees
FROM emp
GROUP BY job;
```

## Q5. Determine the number of managers without listing them.

```sql
SELECT COUNT(DISTINCT mgr) AS "Number of Managers"
FROM emp
WHERE mgr IS NOT NULL;
```

## Q6. Find the difference between the highest and lowest salaries.

```sql
SELECT MAX(sal) - MIN(sal) AS Difference
FROM emp;
```

## Q7. Display the manager number and the salary of the lowest-paid employee for that manager.

```sql
SELECT mgr,
       MIN(sal) AS Lowest_Salary
FROM emp
WHERE mgr IS NOT NULL
GROUP BY mgr
HAVING MIN(sal) > 2000
ORDER BY Lowest_Salary DESC;
```

## Q8. Display the total number of employees and the number of employees hired in 1980, 1981, and 1982.

```sql
SELECT COUNT(*) AS Total_Employees,
       SUM(CASE WHEN EXTRACT(YEAR FROM hiredate)=1980 THEN 1 ELSE 0 END) AS Hired_1980,
       SUM(CASE WHEN EXTRACT(YEAR FROM hiredate)=1981 THEN 1 ELSE 0 END) AS Hired_1981,
       SUM(CASE WHEN EXTRACT(YEAR FROM hiredate)=1982 THEN 1 ELSE 0 END) AS Hired_1982
FROM emp;
```

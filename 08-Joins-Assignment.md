# Displaying Data from Multiple Tables Using Joins - Assignment

## Q1. Write a query for the HR department to produce the addresses of all the departments. Use the EMP and DEPT tables. Show the EMPNO, ENAME, SAL, DNAME and LOC in the output. Use a NATURAL JOIN.

```sql
SELECT empno, ename, sal, dname, loc
FROM emp
NATURAL JOIN dept;
```

---

## Q2. Display the JOB, MGR, SAL, COMM and DNAME of employees whose JOB is SALESMAN. (Equi Join)

```sql
SELECT e.job, e.mgr, e.sal, e.comm, d.dname
FROM emp e, dept d
WHERE e.deptno = d.deptno
AND e.job = 'SALESMAN';
```

---

## Q3. Display the ENAME, JOB, DEPTNO and DNAME for all employees who work in DALLAS. (Equi Join)

```sql
SELECT e.ename, e.job, e.deptno, d.dname
FROM emp e, dept d
WHERE e.deptno = d.deptno
AND d.loc = 'DALLAS';
```

---

## Q4. Display employees' name and employee number along with their manager's name and manager number. Label the columns Employee, Emp#, Manager and Mgr#.

```sql
SELECT e.ename AS "Employee",
       e.empno AS "Emp#",
       m.ename AS "Manager",
       m.empno AS "Mgr#"
FROM emp e
JOIN emp m
ON e.mgr = m.empno;
```

---

## Q5. Modify the previous query to display all employees including KING, who has no manager. Order the results by employee number.

```sql
SELECT e.ename AS "Employee",
       e.empno AS "Emp#",
       m.ename AS "Manager",
       m.empno AS "Mgr#"
FROM emp e
LEFT OUTER JOIN emp m
ON e.mgr = m.empno
ORDER BY e.empno;
```

---

## Q6. Display the employee name, job, department name, salary and grade for all employees. (Non-Equi Join)

```sql
SELECT e.ename,
       e.job,
       d.dname,
       e.sal,
       s.grade
FROM emp e
JOIN dept d
ON e.deptno = d.deptno
JOIN salgrade s
ON e.sal BETWEEN s.losal AND s.hisal;
```

---

## Q7. Display the ENAME and DNAME of all employees. Also display departments that do not have any employees. (Outer Join)

```sql
SELECT e.ename,
       d.dname
FROM emp e
RIGHT OUTER JOIN dept d
ON e.deptno = d.deptno;
```
---

## Q8. Display the names and hire dates for all employees who were hired before their managers, along with their managers' names and hire dates. (Self Join with Outer Join)

```sql
SELECT e.ename AS Employee,
       e.hiredate AS Employee_HireDate,
       m.ename AS Manager,
       m.hiredate AS Manager_HireDate
FROM emp e
LEFT OUTER JOIN emp m
ON e.mgr = m.empno
WHERE e.hiredate < m.hiredate;
```

---

## Q9. Display the EMPNO, ENAME, DNAME, and LOC of employees who are working as CLERK. Use the USING clause.

```sql
SELECT empno, ename, dname, loc
FROM emp
JOIN dept
USING (deptno)
WHERE job = 'CLERK';
```

---

## Q10. Display the ENAME, SAL, MGR, and DNAME of employees whose salary is more than 2000. Use the ON clause.

```sql
SELECT e.ename,
       e.sal,
       e.mgr,
       d.dname
FROM emp e
JOIN dept d
ON e.deptno = d.deptno
WHERE e.sal > 2000;
```

---

## Q11. Display the EMPNO, ENAME, JOB, DEPTNO, DNAME, and LOC of employees. Use LEFT OUTER JOIN.

```sql
SELECT e.empno,
       e.ename,
       e.job,
       e.deptno,
       d.dname,
       d.loc
FROM emp e
LEFT OUTER JOIN dept d
ON e.deptno = d.deptno;
```

---

## Q12. Display the ENAME and DNAME of employees. Use RIGHT OUTER JOIN.

```sql
SELECT e.ename,
       d.dname
FROM emp e
RIGHT OUTER JOIN dept d
ON e.deptno = d.deptno;
```

---

## Q13. Display the EMPNO, DNAME, and LOC of employees. Use FULL OUTER JOIN.

```sql
SELECT e.empno,
       d.dname,
       d.loc
FROM emp e
FULL OUTER JOIN dept d
ON e.deptno = d.deptno;
```

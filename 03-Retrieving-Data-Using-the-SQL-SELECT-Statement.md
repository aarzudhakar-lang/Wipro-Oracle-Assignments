# Retrieving Data Using the SQL SELECT Statement

## Assignment 1

### Question 1
Determine the Structure of DEPT Table and its Contents.

### SQL Commands

```sql
DESC DEPT;

SELECT * FROM DEPT;
```

### Explanation
- `DESC DEPT;` displays the structure of the DEPT table.
- `SELECT * FROM DEPT;` displays all rows of the DEPT table.

---

## Assignment 2

### Question 2
Determine the Structure of EMP Table and its Contents.

### SQL Commands

```sql
DESC EMP;

SELECT * FROM EMP;
```

### Explanation
- `DESC EMP;` displays the structure of the EMP table.
- `SELECT * FROM EMP;` displays all rows of the EMP table.

---

## Assignment 3

### Question 3
Display the ENAME and DEPTNO from EMP table whose EMPNO is 7788.

### SQL Query

```sql
SELECT ENAME, DEPTNO
FROM EMP
WHERE EMPNO = 7788;
```

### Expected Output

| ENAME | DEPTNO |
|--------|--------|
| SCOTT | 20 |

### Explanation
This query displays the employee name and department number of the employee whose employee number is 7788.

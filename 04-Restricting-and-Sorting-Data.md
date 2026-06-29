# Restricting and Sorting Data

## Assignment 1

### Question 1
Display the ENAME, SAL, COMM from EMP table who earn commission and sort the records in descending order of Salary and Comm. Use column's numeric position in the ORDER BY clause.

### SQL Query

```sql
SELECT ENAME, SAL, COMM
FROM EMP
WHERE COMM IS NOT NULL
ORDER BY 2 DESC, 3 DESC;
```

### Explanation
- Displays employee name, salary and commission.
- Shows only employees who earn commission.
- Sorts by Salary (2nd column) and Commission (3rd column) in descending order.

---

## Assignment 2

### Question 2
The HR department needs a query to display all unique job codes from the EMP table.

### SQL Query

```sql
SELECT DISTINCT JOB
FROM EMP;
```

### Explanation
- DISTINCT removes duplicate job titles.
- Displays only unique job codes.

---

## Assignment 3

### Question 3
The HR department wants more descriptive column headings for its report on employees.
Name the column headings Emp #, Employee, Job, and Hire Date respectively by giving Column Alias.

### SQL Query

```sql
SELECT EMPNO AS "Emp #",
       ENAME AS "Employee",
       JOB AS "Job",
       HIREDATE AS "Hire Date"
FROM EMP;
```

### Explanation
- Uses column aliases to display user-friendly headings.

---

## Assignment 4

### Question 4
The HR department has requested a report of all employees and their job IDs.
Display the last name concatenated with the job ID (separated by a comma and space) and name the column Employee and Title by giving Column Alias.

### SQL Query

```sql
SELECT ENAME || ', ' || JOB AS "Employee and Title"
FROM EMP;
```

### Explanation
- Concatenates employee name and job title.
- Uses comma and space as separator.
- Displays the result using the alias "Employee and Title".
- ## Assignment 5

### Question 5
To familiarize yourself with the data in the EMP table, create a query to display all the data from that table. Separate each column output by a comma. ENAME, JOB, HIREDATE, MGR. Name the column title THE_OUTPUT.

### SQL Query

```sql
SELECT ENAME || ', ' || JOB || ', ' || HIREDATE || ', ' || MGR AS "THE_OUTPUT"
FROM EMP;
```

### Explanation
Displays ENAME, JOB, HIREDATE and MGR in a single column separated by commas.

---

## Assignment 6

### Question 6
Create a report to display the ENAME, JOB and HIREDATE for the employees whose name is SCOTT or TURNER. Order the query in ascending order by HIREDATE.

### SQL Query

```sql
SELECT ENAME, JOB, HIREDATE
FROM EMP
WHERE ENAME IN ('SCOTT', 'TURNER')
ORDER BY HIREDATE ASC;
```

### Explanation
Displays employee name, job and hire date of SCOTT and TURNER sorted by hire date.

---

## Assignment 7

### Question 7
Display the ENAME and DEPTNO of all employees in departments 20 or 30 in ascending alphabetical order by ENAME.

### SQL Query

```sql
SELECT ENAME, DEPTNO
FROM EMP
WHERE DEPTNO IN (20, 30)
ORDER BY ENAME ASC;
```

### Explanation
Displays employee name and department number for departments 20 and 30 sorted alphabetically.

---

## Assignment 8

### Question 8
Modify the previous query to display the last name and salary of employees who earn between 2000 and 3000 and are in department 20 or 30. Label the columns Employee and Monthly Salary using Column Alias.

### SQL Query

```sql
SELECT ENAME AS "Employee",
       SAL AS "Monthly Salary"
FROM EMP
WHERE SAL BETWEEN 2000 AND 3000
AND DEPTNO IN (20, 30);
```

### Explanation
Displays employee name and salary for employees whose salary is between 2000 and 3000 and who belong to departments 20 or 30.
## Assignment 9

### Question 9
The HR department needs a report that displays the last name and hire date for all employees who were hired in 1981.

### SQL Query

```sql
SELECT ENAME, HIREDATE
FROM EMP
WHERE HIREDATE BETWEEN
TO_DATE( '01-JAN-81' , 'DD-MON-YYYY')
AND
TO_DATE('31-DEC-1981','DD-MON-YYYY');

```

### Explanation
Displays employee name and hire date of employees hired during the year 1981.

---

## Assignment 10

### Question 10
Display the ENAME and SAL of employees who earn more than an amount the user specifies after a prompt.

### SQL Query

```sql
SELECT ENAME, SAL
FROM EMP
WHERE SAL > &SALARY;
```

### Explanation
Prompts the user to enter a salary amount and displays employees whose salary is greater than that amount.

---

## Assignment 11

### Question 11
Create a report to display the last name and job title of all employees who do not have a manager.

### SQL Query

```sql
SELECT ENAME, JOB
FROM EMP
WHERE MGR IS NULL;
```

### Explanation
Displays employees who do not have a manager.

---

## Assignment 12

### Question 12
Create a query that prompts the user for Manager ID and generates EMPNO, ENAME, SAL, DEPTNO. The user should have the ability to sort the records on a selected column.

### SQL Query

```sql
SELECT EMPNO, ENAME, SAL, DEPTNO
FROM EMP
WHERE MGR = &MANAGER_ID
ORDER BY &SORT_COLUMN;
```

### Explanation
Prompts the user to enter:
- Manager ID
- Column name for sorting

Then displays the matching employee details sorted by the selected column.
## Assignment 13

### Question 13
The HR department wants to run reports based on a manager. Create a query that prompts the user for a MGR and generates the EMPNO, ENAME, SALARY, and DEPTNO for that manager's employees. The HR department wants the ability to sort the report on a selected column.

### SQL Query

```sql
SELECT EMPNO, ENAME, SAL, DEPTNO
FROM EMP
WHERE MGR = &MGR
ORDER BY &SORT_COLUMN;
```

### Explanation
Prompts the user to enter a Manager ID and a column name for sorting the report.

---

## Assignment 14

### Question 14
Display all employee last names in which the third letter of the name is A.

### SQL Query

```sql
SELECT ENAME
FROM EMP
WHERE ENAME LIKE '__A%';
```

### Explanation
The underscore (_) represents one character.
`__A%` means the third character must be 'A'.

---

## Assignment 15

### Question 15
Display the last name of all employees who have both an A and an S in their ENAME.

### SQL Query

```sql
SELECT ENAME
FROM EMP
WHERE ENAME LIKE '%A%'
AND ENAME LIKE '%S%';
```

### Explanation
Displays employee names containing both 'A' and 'S'.

---

## Assignment 16

### Question 16
Display the ENAME, JOB, SAL for all employees whose jobs are CLERK and whose salary is 800 or 950 or 1300.

### SQL Query

```sql
SELECT ENAME, JOB, SAL
FROM EMP
WHERE JOB = 'CLERK'
AND SAL IN (800, 950, 1300);
```

### Explanation
Displays employees whose job is CLERK and whose salary is either 800, 950 or 1300.

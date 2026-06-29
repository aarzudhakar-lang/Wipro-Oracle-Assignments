# Using Single-Row Functions to Customize the Output

## Assignment 1

### Question
Write a query to display the current date. Label the column Date.

### SQL Query

```sql
SELECT SYSDATE AS "Date"
FROM DUAL;
```

### Explanation
Displays the current system date.

---

## Assignment 2

### Question
The HR department needs a report to display the employee number, last name, salary, and salary increased by 15.5% (expressed as a whole number) for each employee. Label the column New Salary.

### SQL Query

```sql
SELECT EMPNO,
       ENAME,
       SAL,
       ROUND(SAL * 1.155) AS "New Salary"
FROM EMP;
```

### Explanation
Calculates the new salary after a 15.5% increase and rounds it to the nearest whole number.

---

## Assignment 3

### Question
Modify the previous query to add a column that subtracts the old salary from the new salary. Label the column Increase.

### SQL Query

```sql
SELECT EMPNO,
       ENAME,
       SAL,
       ROUND(SAL * 1.155) AS "New Salary",
       ROUND(SAL * 1.155) - SAL AS "Increase"
FROM EMP;
```

### Explanation
Displays the salary increase amount after adding 15.5%.

---

## Assignment 4

### Question
Write a query that displays the employee name (first letter uppercase and remaining letters lowercase) and the length of the employee name for employees whose names start with J, A, or M. Give each column an appropriate label. Sort the results by employee name.

### SQL Query

```sql
SELECT INITCAP(ENAME) AS "Employee Name",
       LENGTH(ENAME) AS "Name Length"
FROM EMP
WHERE ENAME LIKE 'J%'
   OR ENAME LIKE 'A%'
   OR ENAME LIKE 'M%'
ORDER BY ENAME;
```

### Explanation
Displays employee names in proper case and their lengths.

---

## Assignment 5

### Question
Rewrite the previous query so that the user is prompted to enter a letter that starts the employee name.

### SQL Query

```sql
SELECT INITCAP(ENAME) AS "Employee Name",
       LENGTH(ENAME) AS "Name Length"
FROM EMP
WHERE ENAME LIKE UPPER('&LETTER') || '%'
ORDER BY ENAME;
```

### Explanation
Prompts the user to enter the starting letter of the employee name.
## Assignment 6

### Question
The HR department wants to find the length of employment for each employee. Display the employee name and calculate the number of months between today and the date on which the employee was hired. Label the column MONTHS_WORKED. Order the results by the number of months worked. Round the number of months to the closest whole number.

### SQL Query

```sql
SELECT ENAME,
       ROUND(MONTHS_BETWEEN(SYSDATE, HIREDATE)) AS MONTHS_WORKED
FROM EMP
ORDER BY MONTHS_WORKED;
```

### Explanation
Calculates the number of months each employee has worked and rounds the result to the nearest whole number.

---

## Assignment 7

### Question
Create a report that produces the following for each employee:
"<employee_name> earns <salary> monthly but wants <3 * salary>."
Label the column Dream Salaries.

### SQL Query

```sql
SELECT ENAME || ' earns ' || SAL ||
       ' monthly but wants ' || (SAL * 3) AS "Dream Salaries"
FROM EMP;
```

### Explanation
Concatenates employee name, current salary and dream salary (3 times the salary).

---

## Assignment 8

### Question
Create a query to display the employee name and salary for all employees. Format the salary to be 15 characters long, left-padded with the $ symbol. Label the column SALARY.

### SQL Query

```sql
SELECT ENAME,
       LPAD(SAL,15,'$') AS "SALARY"
FROM EMP;
```

### Explanation
Displays the salary padded on the left with '$' to a total width of 15 characters.

---

## Assignment 9

### Question
Display each employee's name, hire date, and salary review date, which is the first Monday after six months of service. Label the column REVIEW. Format the date similar to:
Monday, the Thirty-First of July, 2000.

### SQL Query

```sql
SELECT ENAME,
       HIREDATE,
       TO_CHAR(
           NEXT_DAY(ADD_MONTHS(HIREDATE,6),'MONDAY'),
           'Day, "the" DDSP "of" Month, YYYY'
       ) AS REVIEW
FROM EMP;
```

### Explanation
Calculates the first Monday after six months from the hire date and formats it as required.

---

## Assignment 10

### Question
Display the employee name, hire date, and day of the week on which the employee started. Label the column DAY. Order the results by the day of the week, starting with Monday.

### SQL Query

```sql
SELECT ENAME,
       HIREDATE,
       TO_CHAR(HIREDATE,'DAY') AS DAY
FROM EMP
ORDER BY TO_CHAR(HIREDATE,'D');
```

### Explanation
Displays the employee name, hire date and weekday of joining.
## Assignment 11

### Question
Create a query that displays the employees' last names and commission amounts. If an employee does not earn commission, show "No Commission." Label the column COMM.

### SQL Query

```sql
SELECT ENAME,
       NVL(TO_CHAR(COMM), 'No Commission') AS COMM
FROM EMP;
```

### Explanation
- Displays employee name and commission.
- If commission is NULL, "No Commission" is displayed.

---

## Assignment 12

### Question
Create a query that displays the first eight characters of the employees' last names and indicates the amounts of their salaries with asterisks. Each asterisk signifies a thousand dollars. Sort the data in descending order of salary. Label the column EMPLOYEES_AND_THEIR_SALARIES.

### SQL Query

```sql
SELECT RPAD(SUBSTR(ENAME,1,8),
LENGTH(SUBSTR(ENAME,1,8))+
 TRUNC(SAL/1000),'*')
 AS EMPLOYEES_AND_THEIR_SALARIES
FROM EMP
ORDER BY SAL DESC;
```

### Explanation
- Displays the first 8 characters of the employee name.
- Adds one '*' for every thousand dollars of salary.
- Results are sorted in descending order of salary.

---

## Assignment 13

### Question
Using the DECODE function, display the grade of all employees based on JOB using the following mapping:
- PRESIDENT → A
- MANAGER → B
- SALESMAN → C
- CLERK → D
- Others → E

### SQL Query

```sql
SELECT ENAME,
       JOB,
       DECODE(JOB,
              'PRESIDENT','A',
              'MANAGER','B',
              'SALESMAN','C',
              'CLERK','D',
              'E') AS GRADE
FROM EMP;
```

### Explanation
Uses the DECODE function to assign grades based on the employee's job.

---

## Assignment 14

### Question
Rewrite the previous statement using the CASE syntax.

### SQL Query

```sql
SELECT ENAME,
       JOB,
       CASE
           WHEN JOB = 'PRESIDENT' THEN 'A'
           WHEN JOB = 'MANAGER' THEN 'B'
           WHEN JOB = 'SALESMAN' THEN 'C'
           WHEN JOB = 'CLERK' THEN 'D'
           ELSE 'E'
       END AS GRADE
FROM EMP;
```

### Explanation
Uses the CASE expression to assign grades based on the employee's job.

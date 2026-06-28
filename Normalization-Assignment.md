# Database Normalization Assignment

## Assignment 1

### Question 1
Observe the structured of a given EMPLOYEE table as below and suggest if this table can be further Normalized
EMPLOYEE (EMPNO, ENAME, SAL, DEPTNO, DNAME, LOC) Explain what normal form this table is and how you can make this into next normal form.

### Current Normal Form
**Second Normal Form (2NF)**

### Reason
- EMPNO is the Primary Key.
- All non-key attributes depend on the primary key.
- However, there is a **Transitive Dependency**:

```
EMPNO → DEPTNO
DEPTNO → DNAME, LOC
```

Since DNAME and LOC depend on DEPTNO instead of EMPNO, the table is **not in Third Normal Form (3NF).**

### Solution 1 (Convert into 3NF)

#### EMPLOYEE Table

| EMPNO | ENAME | SAL | DEPTNO |
|-------|-------|------|--------|
|101|Rahul|50000|10|
|102|Priya|45000|20|

#### DEPARTMENT Table

| DEPTNO | DNAME | LOC |
|--------|-------|------|
|10|HR|Delhi|
|20|Sales|Mumbai|

### Result
The table is converted into **Third Normal Form (3NF)** by removing the transitive dependency.

---

# Assignment 2

### Question 2 
Observe the structures of a given STUDENT table as below and suggest if this table can be further Normalized
STUDENT (ROLLNO, NAME, AGE, EXAM, MARKS, GRADE) Explain what normal form this table is and how you can make this into next normal form

### Current Normal Form
**Second Normal Form (2NF)**

### Reason
- ROLLNO is the Primary Key.
- There is a **Transitive Dependency**:

```
ROLLNO → MARKS
MARKS → GRADE
```

GRADE depends on MARKS instead of ROLLNO, so the table is **not in Third Normal Form (3NF).**

### Solution 2 (Convert into 3NF)

#### STUDENT Table

| ROLLNO | NAME | AGE | EXAM | MARKS |
|--------|------|-----|------|-------|
|101|Aman|20|DBMS|85|

#### GRADE Table

| MARKS | GRADE |
|-------|-------|
|90-100|A|
|80-89|B|
|70-79|C|

### Result
The table is converted into **Third Normal Form (3NF)** by removing the transitive dependency.

---

# Assignment 3

### Question 3
Observe the structure of a given EMPLOYEE table and suggestwhat kind of problem this table has and how to solve the problem
EMPLOYEE (EMPNO, PROJECT_NO, NO_OF_DAYS, CUSTOMERNAME) In the above table EMPNO AND PROJECT_NO both are together a composite primary key

**Composite Primary Key:** (EMPNO, PROJECT_NO)

### Problem
The table has a **Partial Dependency**.

```
PROJECT_NO → CUSTOMERNAME
```

CUSTOMERNAME depends only on PROJECT_NO and not on the complete composite primary key.

Therefore, the table is **not in Second Normal Form (2NF).**

### Solution 3 (Convert into 2NF)

#### EMPLOYEE_PROJECT Table

| EMPNO | PROJECT_NO | NO_OF_DAYS |
|-------|------------|------------|
|101|P1|30|
|101|P2|15|

#### PROJECT Table

| PROJECT_NO | CUSTOMERNAME |
|------------|--------------|
|P1|TCS|
|P2|Infosys|

### Result
The table is converted into **Second Normal Form (2NF)** by removing the partial dependency.

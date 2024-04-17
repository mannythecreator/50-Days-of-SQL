# Replace Employee ID With The Unique Identifier
\#MySQL

[LeetCode](https://leetcode.com/problems/replace-employee-id-with-the-unique-identifier/?envType=study-plan-v2&envId=top-sql-50)

Runtime beats 63% of users using MySQL

<img width="300" alt="image" src="https://github.com/mannythecreator/50-Days-of-SQL/assets/60325078/27415868-f535-41bc-8467-5279db1c1c97">

```
Table: Employees
+---------------+---------+
| Column Name   | Type    |
+---------------+---------+
| id            | int     |
| name          | varchar |
+---------------+---------+

Table: EmployeeUNI
+---------------+---------+
| Column Name   | Type    |
+---------------+---------+
| id            | int     |
| unique_id     | int     |
+---------------+---------+

```
Employees: id is the primary key (column with unique values) for this table.
Each row of this table contains the id and the name of an employee in a company.

EmployeeUNI: (id, unique_id) is the primary key (combination of columns with unique values) for this table.
Each row of this table contains the id and the corresponding unique id of an employee in the company.

## Task
Write a solution to show the unique ID of each user, If a user does not have a unique ID replace just show null.

Return the result table in any order.

## Database
```
CREATE table If Not Exists Employees (id int, name varchar(20))
CREATE table If Not Exists EmployeeUNI (id int, unique_id int)
TRUNCATE table Employees
INSERT into Employees (id, name) values ('1', 'Alice')
INSERT into Employees (id, name) values ('7', 'Bob')
INSERT into Employees (id, name) values ('11', 'Meir')
INSERT into Employees (id, name) values ('90', 'Winston')
INSERT into Employees (id, name) values ('3', 'Jonathan')
TRUNCATE table EmployeeUNI
INSERT into EmployeeUNI (id, unique_id) values ('3', '1')
INSERT into EmployeeUNI (id, unique_id) values ('11', '2')
INSERT into EmployeeUNI (id, unique_id) values ('90', '3')
```
```
Employees table:
+----+----------+
| id | name     |
+----+----------+
| 1  | Alice    |
| 7  | Bob      |
| 11 | Meir     |
| 90 | Winston  |
| 3  | Jonathan |
+----+----------+

EmployeeUNI table:
+----+-----------+
| id | unique_id |
+----+-----------+
| 3  | 1         |
| 11 | 2         |
| 90 | 3         |
+----+-----------+
```
## Code Solution
```
SELECT unique_id, name
FROM EmployeeUNI
RIGHT JOIN Employees ON Employees.id = EmployeeUNI.id
```
## Output
```
| unique_id | name     |
| --------- | -------- |
| null      | Alice    |
| null      | Bob      |
| 2         | Meir     |
| 3         | Winston  |
| 1         | Jonathan |
```

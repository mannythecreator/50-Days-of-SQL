# Find Employee Bonuses | LEFT JOIN | Boolean Logic
\#MySQL \#Oracle \#PostgreSQL \#MSSQL

[LeetCode](https://leetcode.com/problems/employee-bonus/?envType=study-plan-v2&envId=top-sql-50)

Beats 89% of MySQL users!

<img width="300" alt="image" src="https://github.com/mannythecreator/50-Days-of-SQL/assets/60325078/ba0cf02b-8f27-4f2d-9df1-0083ff257fba">

```
Table: Employee
+-------------+---------+
| Column Name | Type    |
+-------------+---------+
| empId       | int     |
| name        | varchar |
| supervisor  | int     |
| salary      | int     |
+-------------+---------+

Table: Bonus
+-------------+------+
| Column Name | Type |
+-------------+------+
| empId       | int  |
| bonus       | int  |
+-------------+------+
```
Employee Table: empId is the column with unique values for this table.
Each row of this table indicates the name and the ID of an employee in addition to their salary and the id of their manager.
Bonus Table: empId is the column of unique values for this table.
empId is a foreign key (reference column) to empId from the Employee table.
Each row of this table contains the id of an employee and their respective bonus.

## Task
Write a solution to report the name and bonus amount of each employee with a bonus less than 1000.

Return the result table in any order.

## Database
```
Create table If Not Exists Employee (empId int, name varchar(255), supervisor int, salary int)
Create table If Not Exists Bonus (empId int, bonus int)
Truncate table Employee
insert into Employee (empId, name, supervisor, salary) values ('3', 'Brad', 'None', '4000')
insert into Employee (empId, name, supervisor, salary) values ('1', 'John', '3', '1000')
insert into Employee (empId, name, supervisor, salary) values ('2', 'Dan', '3', '2000')
insert into Employee (empId, name, supervisor, salary) values ('4', 'Thomas', '3', '4000')
Truncate table Bonus
insert into Bonus (empId, bonus) values ('2', '500')
insert into Bonus (empId, bonus) values ('4', '2000')
```
```
Table: Employee
+-------+--------+------------+--------+
| empId | name   | supervisor | salary |
+-------+--------+------------+--------+
| 3     | Brad   | null       | 4000   |
| 1     | John   | 3          | 1000   |
| 2     | Dan    | 3          | 2000   |
| 4     | Thomas | 3          | 4000   |
+-------+--------+------------+--------+

Table: Bonus
+-------+-------+
| empId | bonus |
+-------+-------+
| 2     | 500   |
| 4     | 2000  |
+-------+-------+
```
## Code Solution
```
# MySQL, Oracle, PostgreSQL, MSSQL
SELECT E.name, B.bonus
FROM Employee E
LEFT JOIN Bonus B ON E.empId = B.empId
WHERE B.bonus < 1000 OR B.bonus IS NULL;
```
## Output
```
| name | bonus |
| ---- | ----- |
| Dan  | 500   |
| John | null  |
| Brad | null  |
```

# Combine Two Tables
[LeetCode](https://leetcode.com/problems/combine-two-tables/)

```
Table: Person
+-------------+---------+
| Column Name | Type    |
+-------------+---------+
| personId    | int     |
| lastName    | varchar |
| firstName   | varchar |
+-------------+---------+

Table: Address
+-------------+---------+
| Column Name | Type    |
+-------------+---------+
| addressId   | int     |
| personId    | int     |
| city        | varchar |
| state       | varchar |
+-------------+---------+
```
personId is the primary key (column with unique values) for this table.
This table contains information about the ID of some persons and their first and last names.

addressId is the primary key (column with unique values) for this table.
Each row of this table contains information about the city and state of one person with ID = PersonId.

## Task
Write a solution to report the first name, last name, city, and state of each person in the Person table. If the address of a personId is not present in the Address table, report null instead.

Return the result table in any order.

## Database
```
CREATE table If Not Exists Person (personId int, firstName varchar(255), lastName varchar(255))
CREATE table If Not Exists Address (addressId int, personId int, city varchar(255), state varchar(255))
TRUNCATE table Person
INSERT into Person (personId, lastName, firstName) values ('1', 'Wang', 'Allen')
INSERT into Person (personId, lastName, firstName) values ('2', 'Alice', 'Bob')
TRUNCATE table Address
INSERT into Address (addressId, personId, city, state) values ('1', '2', 'New York City', 'New York')
INSERT into Address (addressId, personId, city, state) values ('2', '3', 'Leetcode', 'California')
```
```
Person table:
+----------+----------+-----------+
| personId | lastName | firstName |
+----------+----------+-----------+
| 1        | Wang     | Allen     |
| 2        | Alice    | Bob       |
+----------+----------+-----------+

Address table:
+-----------+----------+---------------+------------+
| addressId | personId | city          | state      |
+-----------+----------+---------------+------------+
| 1         | 2        | New York City | New York   |
| 2         | 3        | Leetcode      | California |
+-----------+----------+---------------+------------+
```
## Code Solution
```
SELECT firstName, lastName, city, state 
FROM Person
LEFT JOIN Address ON Person.personId = Address.personID
```
### Output
```
| firstName | lastName | city          | state    |
| --------- | -------- | ------------- | -------- |
| Allen     | Wang     | null          | null     |
| Bob       | Alice    | New York City | New York |
````

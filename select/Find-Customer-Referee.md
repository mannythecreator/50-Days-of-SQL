# Use Database to Find Customer Referee
\#MySQL

[LeetCode](https://leetcode.com/problems/find-customer-referee/)

```
Table: Customer
+-------------+---------+
| Column Name | Type    |
+-------------+---------+
| id          | int     |
| name        | varchar |
| referee_id  | int     |
+-------------+---------+
```
In SQL, id is the primary key column for this table.
Each row of this table indicates the id of a customer, their name, and the id of the customer who referred them.

## Task
Find the names of the customer that are not referred by the customer with id = 2.
Return the result table in any order.

### Database Example
```
Input:
CREATE table If Not Exists Customer (id int, name varchar(25), referee_id int)
Truncate table Customer
INSERT into Customer (id, name, referee_id) values ('1', 'Will', 'None')
INSERT into Customer (id, name, referee_id) values ('2', 'Jane', 'None')
INSERT into Customer (id, name, referee_id) values ('3', 'Alex', '2')
INSERT into Customer (id, name, referee_id) values ('4', 'Bill', 'None')
INSERT into Customer (id, name, referee_id) values ('5', 'Zack', '1')
INSERT into Customer (id, name, referee_id) values ('6', 'Mark', '2')
```
```
Table: Customer:
+----+------+------------+
| id | name | referee_id |
+----+------+------------+
| 1  | Will | null       |
| 2  | Jane | null       |
| 3  | Alex | 2          |
| 4  | Bill | null       |
| 5  | Zack | 1          |
| 6  | Mark | 2          |
+----+------+------------+
```

## Code Solution
```
SELECT name FROM Customer
WHERE referee_id != 2 OR referee_id is null
```
```
Output: 
+------+
| name |
+------+
| Will |
| Jane |
| Bill |
| Zack |
+------+
```

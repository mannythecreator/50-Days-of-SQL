# Customer Who Visited But Did Not Make Any Transactions | LEFT JOIN | Creating Columns | Grouping
\#MySQL \#MSSQL \#Oracle \#PostgreSQL

[LeetCode](https://leetcode.com/problems/customer-who-visited-but-did-not-make-any-transactions/description/?envType=study-plan-v2&envId=top-sql-50)

Beats 91% of MySQL users, 92% of MSSQL users, 94% of Oracle users!

<img width="300" alt="Runtime beats 91.12% of users with MySQL" src="https://github.com/mannythecreator/50-Days-of-SQL/assets/60325078/b681fae0-09c6-477c-9630-e1eb1a580170">
<img width="300" alt="Runtime beats 94% of users with Orcale" src="https://github.com/mannythecreator/50-Days-of-SQL/assets/60325078/0a668db6-c1aa-4c67-b087-68fd58e5bbce">


```
Table: Visits
+-------------+---------+
| Column Name | Type    |
+-------------+---------+
| visit_id    | int     |
| customer_id | int     |
+-------------+---------+

Table: Transactions
+----------------+---------+
| Column Name    | Type    |
+----------------+---------+
| transaction_id | int     |
| visit_id       | int     |
| amount         | int     |
+----------------+---------+
```
Visits: visit_id is the column with unique values for this table.
This table contains information about the customers who visited the mall.

Transactions: transaction_id is column with unique values for this table.
This table contains information about the transactions made during the visit_id.

## Task
Write a solution to find the IDs of the users who visited without making any transactions and the number of times they made these types of visits.

Return the result table sorted in any order.

## Database
```
CREATE table IF NOT Exists Visits(visit_id int, customer_id int)
CREATE table IF NOT Exists Transactions(transaction_id int, visit_id int, amount int)
TRUNCATE table Visits
INSERT INTO Visits (visit_id, customer_id) values ('1', '23')
INSERT INTO Visits (visit_id, customer_id) values ('2', '9')
INSERT INTO Visits (visit_id, customer_id) values ('4', '30')
INSERT INTO Visits (visit_id, customer_id) values ('5', '54')
INSERT INTO Visits (visit_id, customer_id) values ('6', '96')
INSERT INTO Visits (visit_id, customer_id) values ('7', '54')
INSERT INTO Visits (visit_id, customer_id) values ('8', '54')
TRUNCATE table Transactions
INSERT INTO Transactions (transaction_id, visit_id, amount) values ('2', '5', '310')
INSERT INTO Transactions (transaction_id, visit_id, amount) values ('3', '5', '300')
INSERT INTO Transactions (transaction_id, visit_id, amount) values ('9', '5', '200')
INSERT INTO Transactions (transaction_id, visit_id, amount) values ('12', '1', '910')
INSERT INTO Transactions (transaction_id, visit_id, amount) values ('13', '2', '970')
```
```
Table: Visits
+----------+-------------+
| visit_id | customer_id |
+----------+-------------+
| 1        | 23          |
| 2        | 9           |
| 4        | 30          |
| 5        | 54          |
| 6        | 96          |
| 7        | 54          |
| 8        | 54          |
+----------+-------------+
Table: Transactions
+----------------+----------+--------+
| transaction_id | visit_id | amount |
+----------------+----------+--------+
| 2              | 5        | 310    |
| 3              | 5        | 300    |
| 9              | 5        | 200    |
| 12             | 1        | 910    |
| 13             | 2        | 970    |
+----------------+----------+--------+
```
## Code Solution
```
# MySQL, MSSQL Server, Oracle, PostgreSQL
SELECT customer_id, COUNT(V.visit_id) AS count_no_trans
FROM Visits V
LEFT JOIN Transactions T ON V.visit_id = T.visit_id
WHERE V.visit_id NOT IN (SELECT visit_id FROM Transactions)
GROUP BY customer_id;
```
## Output
```
| customer_id | count_no_trans |
| ----------- | -------------- |
| 30          | 1              |
| 96          | 1              |
| 54          | 2              |
```

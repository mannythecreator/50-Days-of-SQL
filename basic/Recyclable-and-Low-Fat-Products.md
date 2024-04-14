# Recyclable and Low Fat Products
\#MySQL

Runtime beat 77% of MySQL users

<img width="400" alt="image" src="https://github.com/mannythecreator/SQL-Practice/assets/60325078/625ca259-0f5d-476a-9027-75f42174c40b">

```
Table: Products
+-------------+---------+
| Column Name | Type    |
+-------------+---------+
| product_id  | int     |
| low_fats    | enum    |
| recyclable  | enum    |
+-------------+---------+
```
product_id is the primary key (column with unique values) for this table.
low_fats is an ENUM (category) of type ('Y', 'N') where 'Y' means this product is low fat and 'N' means it is not.
recyclable is an ENUM (category) of types ('Y', 'N') where 'Y' means this product is recyclable and 'N' means it is not.

## Task
Write a solution to find the ids of products that are both low fat and recyclable.

Return the result table in any order.

## Database
```
CREATE table If Not Exists Products (product_id int, low_fats ENUM('Y', 'N'), recyclable ENUM('Y','N'))
TRUNCATE table Products
INSERT into Products (product_id, low_fats, recyclable) values ('0', 'Y', 'N')
INSERT into Products (product_id, low_fats, recyclable) values ('1', 'Y', 'Y')
INSERT into Products (product_id, low_fats, recyclable) values ('2', 'N', 'Y')
INSERT into Products (product_id, low_fats, recyclable) values ('3', 'Y', 'Y')
INSERT into Products (product_id, low_fats, recyclable) values ('4', 'N', 'N')
```
```
Table Products:
+-------------+----------+------------+
| product_id  | low_fats | recyclable |
+-------------+----------+------------+
| 0           | Y        | N          |
| 1           | Y        | Y          |
| 2           | N        | Y          |
| 3           | Y        | Y          |
| 4           | N        | N          |
+-------------+----------+------------+
```
## Code Solution
```
SELECT product_id FROM Products
WHERE (low_fats = "Y") AND (recyclable = "Y")
```
## Output
```
| product_id |
| ---------- |
| 1          |
| 3          |
```

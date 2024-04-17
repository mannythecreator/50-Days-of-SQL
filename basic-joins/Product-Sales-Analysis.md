# Product Sales Analysis I
\#MySQL \#Oracle

[LeetCode](https://leetcode.com/problems/product-sales-analysis-i/description/?envType=study-plan-v2&envId=top-sql-50)

Beats 95% of Oracle users

<img width="300" alt="Beats 94.73% of users with Oracle" src="https://github.com/mannythecreator/50-Days-of-SQL/assets/60325078/f6078198-0339-410b-898d-ccf9d671cdab">

```
Table: Sales
+-------------+-------+
| Column Name | Type  |
+-------------+-------+
| sale_id     | int   |
| product_id  | int   |
| year        | int   |
| quantity    | int   |
| price       | int   |
+-------------+-------+
Table: Product
+--------------+---------+
| Column Name  | Type    |
+--------------+---------+
| product_id   | int     |
| product_name | varchar |
+--------------+---------+
```
Sales: (sale_id, year) is the primary key (combination of columns with unique values) of this table.
product_id is a foreign key (reference column) to Product table.
Each row of this table shows a sale on the product product_id in a certain year.
Note that the price is per unit.
Product: product_id is the primary key (column with unique values) of this table.
Each row of this table indicates the product name of each product.
## Task
Write a solution to report the product_name, year, and price for each sale_id in the Sales table.

Return the resulting table in any order.
## Database
```
CREATE table If Not Exists Sales (sale_id int, product_id int, year int, quantity int, price int)
CREATE table If Not Exists Product (product_id int, product_name varchar(10))
TRUNCATE table Sales
INSERT into Sales (sale_id, product_id, year, quantity, price) values ('1', '100', '2008', '10', '5000')
INSERT into Sales (sale_id, product_id, year, quantity, price) values ('2', '100', '2009', '12', '5000')
INSERT into Sales (sale_id, product_id, year, quantity, price) values ('7', '200', '2011', '15', '9000')
TRUNCATE table Product
INSERT into Product (product_id, product_name) values ('100', 'Nokia')
INSERT into Product (product_id, product_name) values ('200', 'Apple')
INSERT into Product (product_id, product_name) values ('300', 'Samsung')
```
```
Sales table:
+---------+------------+------+----------+-------+
| sale_id | product_id | year | quantity | price |
+---------+------------+------+----------+-------+ 
| 1       | 100        | 2008 | 10       | 5000  |
| 2       | 100        | 2009 | 12       | 5000  |
| 7       | 200        | 2011 | 15       | 9000  |
+---------+------------+------+----------+-------+
Product table:
+------------+--------------+
| product_id | product_name |
+------------+--------------+
| 100        | Nokia        |
| 200        | Apple        |
| 300        | Samsung      |
+------------+--------------+
```
## Code Solution
```
# MySQL, Oracle
SELECT product_name, year, price
FROM Sales
LEFT JOIN Product 
ON Sales.product_id = Product.product_id;
```
## Output
```
| product_name | year | price |
| ------------ | ---- | ----- |
| Nokia        | 2008 | 5000  |
| Nokia        | 2009 | 5000  |
| Apple        | 2011 | 9000  |
```

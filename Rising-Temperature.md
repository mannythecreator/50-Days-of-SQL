# Rising Temperature

[LeetCode](https://leetcode.com/problems/rising-temperature/?envType=study-plan-v2&envId=top-sql-50)

```
Table: Weather
+---------------+---------+
| Column Name   | Type    |
+---------------+---------+
| id            | int     |
| recordDate    | date    |
| temperature   | int     |
+---------------+---------+
```
id is the column with unique values for this table.
There are no different rows with the same recordDate.
This table contains information about the temperature on a certain day.

## Task
Write a solution to find all dates' Id with higher temperatures compared to its previous dates (yesterday).

Return the result table in any order.

## Database
```
CREATE table If Not Exists Weather (id int, recordDate date, temperature int)
TRUNCATE table Weather
INSERT INTO Weather (id, recordDate, temperature) values ('1', '2015-01-01', '10')
INSERT INTO Weather (id, recordDate, temperature) values ('2', '2015-01-02', '25')
INSERT INTO Weather (id, recordDate, temperature) values ('3', '2015-01-03', '20')
INSERT INTO Weather (id, recordDate, temperature) values ('4', '2015-01-04', '30')
```
```
Table: Weather
+----+------------+-------------+
| id | recordDate | temperature |
+----+------------+-------------+
| 1  | 2015-01-01 | 10          |
| 2  | 2015-01-02 | 25          |
| 3  | 2015-01-03 | 20          |
| 4  | 2015-01-04 | 30          |
+----+------------+-------------+
```

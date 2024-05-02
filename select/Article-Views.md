# Find Duplicate Article Views | DISTINCT
\#MySQL

[LeetCode](https://leetcode.com/problems/article-views-i/?envType=study-plan-v2&envId=top-sql-50)

```
Table: Views
+---------------+---------+
| Column Name   | Type    |
+---------------+---------+
| article_id    | int     |
| author_id     | int     |
| viewer_id     | int     |
| view_date     | date    |
+---------------+---------+
```
There is no primary key (column with unique values) for this table, the table may have duplicate rows.
Each row of this table indicates that some viewer viewed an article (written by some author) on some date. 
Note that equal author_id and viewer_id indicate the same person.

## Task
Write a solution to find all the authors that viewed at least one of their own articles.

Return the result table sorted by id in ascending order.

## Database
```
CREATE table If Not Exists Views (article_id int, author_id int, viewer_id int, view_date date)
TRUNCATE table Views
INSERT into Views (article_id, author_id, viewer_id, view_date) values ('1', '3', '5', '2019-08-01')
INSERT into Views (article_id, author_id, viewer_id, view_date) values ('1', '3', '6', '2019-08-02')
INSERT into Views (article_id, author_id, viewer_id, view_date) values ('2', '7', '7', '2019-08-01')
INSERT into Views (article_id, author_id, viewer_id, view_date) values ('2', '7', '6', '2019-08-02')
INSERT into Views (article_id, author_id, viewer_id, view_date) values ('4', '7', '1', '2019-07-22')
INSERT into Views (article_id, author_id, viewer_id, view_date) values ('3', '4', '4', '2019-07-21')
INSERT into Views (article_id, author_id, viewer_id, view_date) values ('3', '4', '4', '2019-07-21')
```
```
Table: Views
+------------+-----------+-----------+------------+
| article_id | author_id | viewer_id | view_date  |
+------------+-----------+-----------+------------+
| 1          | 3         | 5         | 2019-08-01 |
| 1          | 3         | 6         | 2019-08-02 |
| 2          | 7         | 7         | 2019-08-01 |
| 2          | 7         | 6         | 2019-08-02 |
| 4          | 7         | 1         | 2019-07-22 |
| 3          | 4         | 4         | 2019-07-21 |
| 3          | 4         | 4         | 2019-07-21 |
+------------+-----------+-----------+------------+
```
## Code Solution
```
SELECT DISTINCT author_id AS id FROM Views
WHERE author_id = viewer_id
ORDER BY id ASC
```
## Output
```
| id |
| -- |
| 4  |
| 7  |
```

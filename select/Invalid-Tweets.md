# Find Invalid Tweets
\#MySQL

[LeetCode](https://leetcode.com/problems/invalid-tweets/?envType=study-plan-v2&envId=top-sql-50)

```
Table: Tweets
+----------------+---------+
| Column Name    | Type    |
+----------------+---------+
| tweet_id       | int     |
| content        | varchar |
+----------------+---------+
```
tweet_id is the primary key (column with unique values) for this table.
This table contains all the tweets in a social media app.

## Task
Write a solution to find the IDs of the invalid tweets. The tweet is invalid if the number of characters used in the content of the tweet is strictly greater than 15.

Return the result table in any order.
## Database
```
CREATE table If Not Exists Tweets(tweet_id int, content varchar(50))
TRUNCATE table Tweets
INSERT into Tweets (tweet_id, content) values ('1', 'Vote for Biden')
INSERT into Tweets (tweet_id, content) values ('2', 'Let us make America great again!')
```
```
Tweets table:
+----------+----------------------------------+
| tweet_id | content                          |
+----------+----------------------------------+
| 1        | Vote for Biden                   |
| 2        | Let us make America great again! |
+----------+----------------------------------+
```
## Code Solution
```
SELECT tweet_id FROM Tweets
WHERE length(content) > 15
```
## Output
```
+----------+
| tweet_id |
+----------+
| 2        |
+----------+
```

# Students and Examinations | CROSS JOIN | LEFT JOIN

[LeetCode](https://leetcode.com/problems/students-and-examinations/?envType=study-plan-v2&envId=top-sql-50)

```
Table: Students
+---------------+---------+
| Column Name   | Type    |
+---------------+---------+
| student_id    | int     |
| student_name  | varchar |
+---------------+---------+

Table: Subjects
+--------------+---------+
| Column Name  | Type    |
+--------------+---------+
| subject_name | varchar |
+--------------+---------+

Table: Examinations
+--------------+---------+
| Column Name  | Type    |
+--------------+---------+
| student_id   | int     |
| subject_name | varchar |
+--------------+---------+
```

Students: student_id is the primary key (column with unique values) for this table.
Each row of this table contains the ID and the name of one student in the school.

Subjects: subject_name is the primary key (column with unique values) for this table.
Each row of this table contains the name of one subject in the school.

Examinations: There is no primary key (column with unique values) for this table. It may contain duplicates.
Each student from the Students table takes every course from the Subjects table.
Each row of this table indicates that a student with ID student_id attended the exam of subject_name.

## Task 
Write a solution to find the number of times each student attended each exam.

Return the result table ordered by student_id and subject_name.

## Database Schema
```
Create table If Not Exists Students (student_id int, student_name varchar(20))
Create table If Not Exists Subjects (subject_name varchar(20))
Create table If Not Exists Examinations (student_id int, subject_name varchar(20))
Truncate table Students
insert into Students (student_id, student_name) values ('1', 'Alice')
insert into Students (student_id, student_name) values ('2', 'Bob')
insert into Students (student_id, student_name) values ('13', 'John')
insert into Students (student_id, student_name) values ('6', 'Alex')
Truncate table Subjects
insert into Subjects (subject_name) values ('Math')
insert into Subjects (subject_name) values ('Physics')
insert into Subjects (subject_name) values ('Programming')
Truncate table Examinations
insert into Examinations (student_id, subject_name) values ('1', 'Math')
insert into Examinations (student_id, subject_name) values ('1', 'Physics')
insert into Examinations (student_id, subject_name) values ('1', 'Programming')
insert into Examinations (student_id, subject_name) values ('2', 'Programming')
insert into Examinations (student_id, subject_name) values ('1', 'Physics')
insert into Examinations (student_id, subject_name) values ('1', 'Math')
insert into Examinations (student_id, subject_name) values ('13', 'Math')
insert into Examinations (student_id, subject_name) values ('13', 'Programming')
insert into Examinations (student_id, subject_name) values ('13', 'Physics')
insert into Examinations (student_id, subject_name) values ('2', 'Math')
insert into Examinations (student_id, subject_name) values ('1', 'Math')
```

## Code Solution
```
# MySQL
SELECT Stu.student_id, Stu.student_name, Sub.subject_name, COUNT(E.subject_name) AS attended_exams
FROM Students Stu
CROSS JOIN Subjects Sub
LEFT JOIN Examinations E ON Stu.student_id = E.student_id AND Sub.subject_name = E.subject_name
GROUP BY Stu.student_id, Stu.student_name, Sub.subject_name
ORDER BY Stu.student_id, Sub.subject_name;
```
## Output
```
| student_id | student_name | subject_name | attended_exams |
| ---------- | ------------ | ------------ | -------------- |
| 1          | Alice        | Math         | 3              |
| 1          | Alice        | Physics      | 2              |
| 1          | Alice        | Programming  | 1              |
| 2          | Bob          | Math         | 1              |
| 2          | Bob          | Physics      | 0              |
| 2          | Bob          | Programming  | 1              |
| 6          | Alex         | Math         | 0              |
| 6          | Alex         | Physics      | 0              |
| 6          | Alex         | Programming  | 0              |
| 13         | John         | Math         | 1              |
| 13         | John         | Physics      | 1              |
| 13         | John         | Programming  | 1              |
```

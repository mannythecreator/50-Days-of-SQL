# Recyclable and Low Fat Products
###### MySQL

Runtime beat 77% of MySQL users

<img width="448" alt="image" src="https://github.com/mannythecreator/SQL-Practice/assets/60325078/625ca259-0f5d-476a-9027-75f42174c40b">

## Task

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

## Code Solution
```
SELECT product_id FROM Products
WHERE (low_fats = "Y") AND (recyclable = "Y")
```

# Database

## Question 1

Given two tables (Departments and Employees). Write a method to find the number of employees in each department.

```sql
SELECT Dept_Name, Departments.Dept_ID, count(*) as ‘num_employees’
FROM Departments
LEFT JOIN Employees
ON  Employees.Dept_ID = Departments.Dept_ID
GROUP BY Departments.Dept_ID, Dept_Name

```

## Question 2

What are the different types of joins? Explain how they differ and why certain types are better in certain situation.


You can use these tables to argue

Table 1 : Regular Beverages
| Name   |      Code      |  
|----------|:-------------:|
| Budweiser |  BUDWEISER | 
| Coca-Cola  |    COCACOLA   |
| Pepsi | PEPSI |


Table 2: Calorie-Free Beverages
| Name   |      Code      |  
|----------|:-------------:|
| Budweiser |  COCACOLA | 
| Coca-Cola  |    FRESCA   |
| Diet Pepsi | PEPSI |
| Pepsi Light | PEPSI |
| Purified Water | Water |


### Solution



**JOIN** is used to combine the results of two tables To perform a join, each of the tables must have at least one field which will be used to find matching records from the other table The join type defines which records will go into the result set.


1. INNER JOIN: Result set will contain only those data where the criteria match 

In our example we will get 3 records: 1 with COCACOLA and 2 with PEPSI codes

2. OUTER JOIN: OUTER JOIN will always contain the results of INNER JOIN, however it can contain some records that have no matching record in other table OUTER JOINs are divided to following subtypes

3. LEFT OUTER JOIN, or simply LEFT JOIN: The result will contain all records from the left table If no matching records were found in the right table, then its fields will contain the NULL values 

In our example, we would get 4 records In addition to INNER JOIN results, BUDWEISER will be listed, because it was in the left table.

4. RIGHT OUTER JOIN, or simply RIGHT JOIN: This type of join is the opposite of LEFT
JOIN; it will contain all records from the right table, and missing fields from the left table will contain NULL If we have two tables A and B, then we can say that statement A LEFT JOIN B is equivalent to statement B RIGHT JOIN A

In our example, we will get 5 records In addition to INNER JOIN results, FRESCA and WATER records will be listed.

5. FULL OUTER JOIN
This type of join combines the results of LEFT and RIGHT joins All records from both tables
will be part of the result set, whether the matching record exists in the other table or not If
no matching record was found then the corresponding result fields will have a NULL value

In our example, we will get 6 records.
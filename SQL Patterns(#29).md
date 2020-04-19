# SQL Patterns
Suppose you're given the following table, called 'employees':

name | job_role
------------ | -------------
John | Analyst
Harry | Administrative Business Partner
Sam | Software Engineer
Tina | Analyst

We want to write a query that returns the name and job_role of each individual
who has either a name that contains 'a' or a job role that ends in the letters 'er'.

Solution:
````sql
SELECT name, job_role FROM employees 
WHERE name LIKE '%a%'
AND job_role LIKE '%er'
````
This simple query makes use of **pattern matching** in SQL. Pattern
matching uses wildcard characters to match different combinations of characters.
The LIKE keyword is used to find a matching string in the given column.

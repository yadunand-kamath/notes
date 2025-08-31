
#sql

## Contents :-

#### [[#4.01 - Databases]]
#### [[#4.02 - SQL Queries]]
#### [[#4.03 - SQL Joins]]

---

## 4.01 - Databases

- **Database** - an organized collection of information or data.
- **Relational Database** - a structured database containing tables that are related to each other.
- **Primary Key** - a column where every row has a unique entry.
- **Foreign Key** - a column in a table that is a primary key in another table.
- **SQL**(***Structured Query Language***) - a programming language used to create, interact with, and request information from a database.
- **Query** - a request for data from database table(s).

---

#sql

## 4.02 - SQL Queries

- **Filtering** - selecting data that match a certain condition
- **Operator** - a symbol or keyword that represents an operation
- **Wildcard** - a special character that can be substituted with any other character. ( % , _ )

### SQL Commands

- `SELECT`: indicates which columns to return
- `FROM`: indicates which table to query
- `ORDER BY`: sequences the records returned by a query based on specific column(s), either in ascending or descending
- `WHERE`: indicates the condition for a filter
- `LIKE`: used with WHERE to search for a pattern in a column
- `BETWEEN`: filters for numbers or dates  within a range
- `AND`: specifies both conditions must be met simultaneously
	![[SQL - AND condition.png]]

- `OR`: specifies that either condition can be met 
	![[SQL - OR condition.png]]

- `NOT`: negates a condition 
	![[SQL - NOT condition.png]]

---

#sql-joins

## 4.03 - SQL Joins

## SQL Joins

1. `INNER JOIN`: returns rows matching on a specified column that exists in more than one table.
	![[SQL - Inner join.png]]

2. `LEFT JOIN`: returns all the records of the first table, but only returns rows of the second table that match on a specified column.
	![[SQL - Left join.png]]

3. `RIGHT JOIN`: returns all of the records of the second table, but only returns rows from the first table that match on a specified column.
	![[SQL - Right join.png]]
4. `FULL OUTER JOIN`: returns all records from both tables. You can think of it as a way of completely merging two tables.
	![[SQL - Full outer join.png]]

---

## 4.04 - Aggregate Functions

**Aggregate functions** are functions that perform a calculation over multiple data points and return the result of the calculation. The actual data is not returned. 

There are various aggregate functions that perform different calculations:

- `COUNT`: returns a single number that represents the number of rows returned from your query.
- `AVG`: returns a single number that represents the average of the numerical data in a column.
- `SUM`: returns a single number that represents the sum of the numerical data in a column. 

### Aggregate function syntax

To use an aggregate function, place the keyword for it after the SELECT keyword, and then in parentheses, indicate the column you want to perform the calculation on.

---
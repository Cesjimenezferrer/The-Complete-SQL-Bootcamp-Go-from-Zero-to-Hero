# The Complete SQL Bootcamp Go from Zero to Hero
## This course aim to teach me  to read and write complex queries to a database using one of the most in demand skills - PostgreSQL. These skills are also applicable to any other major SQL database, such as MySQL, Microsoft SQL Server, Amazon Redshift, Oracle, and much more.

**Below are the exercises and what I learned from each:**

1. Return the customer IDs of customers who have spent at least $110 with the staff member who has an ID of 2.
   
*Learned about the GROUP BY and HAVING clauses to aggregate data and apply conditions to those groups.*
```
SELECT customer_id, SUM(amount)
FROM payment
WHERE staff_id = 2
GROUP BY customer_id
HAVING SUM(amount) > 110;
```

2. How many films begin with the letter J?
   
*Learned how to use the LIKE operator to perform pattern matching in SQL.*
```
SELECT title FROM film
WHERE title LIKE 'J%';
```
3. What customer has the highest customer ID number whose name starts with an 'E' and has an address ID lower than 500?
   
*Learned how to combine conditions in the WHERE clause and use ORDER BY to sort data.*
```
SELECT first_name
FROM customer
WHERE first_name LIKE 'E%'
AND address_id < 500
ORDER BY customer_id DESC
LIMIT 1;
```
4. JOIN Challenges: Alert customers in California about sales tax changes.
   
*Gained experience with JOIN statements to combine data from multiple tables and retrieve specific fields.*
```
SELECT customer.email, address.district 
FROM customer
JOIN address ON customer.address_id = address.address_id
WHERE address.district = 'California';
```
5. Date Stamp: Identify payment months and payments made on Mondays.
   
*Learned how to use SQL functions to extract specific components from dates and format them.*
```
SELECT DISTINCT(TO_CHAR(payment_date,'MONTH'))
FROM payment;

SELECT COUNT(*)
FROM payment
WHERE EXTRACT(dow FROM payment_date) = 1;
```

6. Retrieve all information from the cd.facilities table.
   
*Practiced basic SELECT queries to retrieve all columns from a table.*
```
SELECT * FROM cd.facilities;
```
7. Print a list of all facilities and their cost to members.
   
*Focused on selecting specific columns from a table.*
```
SELECT name, membercost 
FROM cd.facilities;
```
8. Produce a list of facilities that charge a fee to members.
   
*Learned how to filter results using the WHERE clause.*
```
SELECT * 
FROM cd.facilities
WHERE membercost > 0;
```
9. List facilities that charge a fee to members and have a fee less than 1/50th of the monthly maintenance cost.
   
*Learned how to compare columns within a single table using arithmetic operators.*
```
SELECT facid, name, membercost, monthlymaintenance
FROM cd.facilities
WHERE membercost > 0 
AND membercost < monthlymaintenance / 50.0;
```
10. Produce a list of all facilities with 'Tennis' in their name.
   
*Utilized the LIKE operator to find patterns within text data.*
```
SELECT * 
FROM cd.facilities
WHERE name LIKE '%Tennis%';
```
11. Retrieve details of facilities with ID 1 and 5 without using the OR operator.
   
*Learned how to use the IN operator to match multiple values in a column.*
```
SELECT * 
FROM cd.facilities
WHERE facid IN (1,5);
```
12. Produce a list of members who joined after September 2012.
   
*Practiced querying data based on date comparisons.*

```
SELECT memid, surname, firstname, joindate 
FROM cd.members
WHERE joindate >= '2012-09-01';
```
13. Produce an ordered list of the first 10 unique surnames from the members table.
   
*Learned how to remove duplicates and sort data using DISTINCT and ORDER BY clauses.*
```
SELECT DISTINCT surname 
FROM cd.members
ORDER BY surname 
LIMIT 10;
```
## This repository contains the exercises I completed as part of the "The Complete SQL Bootcamp - Go from Zero to Hero" course on Udemy (9 hours of learning). Through these challenges, I have developed a strong understanding of various SQL concepts including querying data, using joins, manipulating datasets, and working with date stamps.

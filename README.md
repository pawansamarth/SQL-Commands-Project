-- Que.1)Identify the primary keys and foreign keys in mavenmovies db. Discuss the differences.
-- The major difference between Primary key and foreign key is Primary keys uniquely identify a record in a table, 
--  while foreign keys establish a link between tables. 
use mavenmovies;
select TABLE_NAME, COLUMN_NAME 
FROM
information_schema.KEY_COLUMN_USAGE
WHERE CONSTRAINT_NAME='PRIMARY'
AND TABLE_SCHEMA ='mavenmovies';

select
constraint_name
table_name,
column_name,
referenced_table_name,
referenced_column_name
from
 information_schema.KEY_column_usage 
where
constraint_name!='PRIMARY'
 AND referenced_table_name is not 
 null
  and Table_SCHEMA ='mavenmovies';

-- Que.2)List all details of actors?
select * from actor;

-- Que.3)List all customer information from db?
select * from customer;
 
-- Que.4) List different countries?
select distinct country from country;
 
-- Que.5)Display all active customers?
select * from customer where active=1;
 
-- Que.6)List of all rental IDs for customer with ID 1.
select customer_id, rental_id from rental where customer_id=1;
 
-- Que.7) Display all the films whose rental duration is greater than 5?
select film_id, title, rental_duration from film where rental_duration>5;
 
-- Que.8)List the total number of films whose replacement cost is greater than $15 & less than $20?
select count(*) as total_film from film where replacement_cost between 15 and 20;
 
-- Que.9)Find the number of films whose rental rate is less than $1?
select count(*) as no_of_films from film where rental_rate <1;

-- Que.10)Display the count of unique first names of actors.
select COUNT(DISTINCT first_name) from actor;

-- Que.11)Display the first 10 records from the customer table?
select * from CUSTOMER limit 10;
  
-- Que.12)Display the first 3 records from the customer table whose first name starts with 'b'?
select * from customer where first_name LIKE 'b%' LIMIT 3;

-- Que.13)Display the names of the first 5 movies which are rated as 'G' ?
select title from film where rating = 'G' LIMIT 5;

-- Que.14)Find all the customers whose first name starts with "a" ?
select * from customer where first_name LIKE "a%";

-- Que.15)Find all customers whose first name ends with "a"?
select * from customer where first_name LIKE "%a";

-- Que.16)Display the list of first 4 cities which start and end with 'a' ?
select city from city where city LIKE 'a%%a' LIMIT 4;

-- Que.17)Find all customers whose first name have "NI" in any position ?
select first_name from customer where first_name LIKE '%ni%';

-- Que.18)Find all customers whose first name have "r" in the second position ?
select first_name from customer where first_name like "_r%";

-- Que.19)Find all customers whose first name starts with "a" & are atleast 5 characters in length ?
select first_name from customer where first_name like 'a%' and length(first_name)>=5;

-- Que.20)Find all customers whose first name starts with "a" and ends with "o" ?
select first_name from customer where first_name like "a%o";

-- Que.21)Get the films with pg and pg-13 rating using IN operator?
select title, rating from film where rating in ("pg","pg-13");

-- Que.22)Get the films with length between 50 to 100 using between operator.
select title,length from film where length between 50 and 100;

-- Que.23) Get the top 50 actors using limit operator ?
select*from actor order by actor_id ASC limit 50;

-- Que.24)Get the distinct film ids from inventory table ?
select distinct film_id from inventory;

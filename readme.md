# RDBMS

Relation Database Management System is the DBMS that stores the data in a structured format known as table and that table further structured the data into the rows and column.

## ROW

row is the horizontal entity also know as record that keep record of individual entries in one row.

## COLUMN

it is vertical entity or each individual entry in a row is known as column.

| Row  | column1 | column2 | column3 |
| :--: | :-----: | :-----: | :-----: |
| Row1 | entry1  | entry2  | entry3  |
| Row2 | entry1  | entry2  | entry3  |

**Database** -> it is a collection of data that is organized.

**SQL(Structured Query Language)** -> it is language that support database.

**MySQL** -> a program that understand SQL.

**QUERY** -> it is command or instruction to instruct.

# SQL Queries ->

> 1.  SHOW DATABASES;

> 2.  USE DATABASE 'NAME';

> 3.  SHOW TABLES;

> 4.  SHOW COLUMNS FROM 'TABLE NAME';

> 5.  SELECT 'COLUMN NAME' FROM 'TABLE NAME';

>     you can select multiple columns by insert between them a (,) .eg ->
>     SELECT c1, c2 FROM 'TABLE NAME';

> or you can select all columns from table using wild card (\*) . eg ->
> SELECT \* FROM 'TABLE NAME';

> 6.  SELECT DISTINCT 'COLUMN NAME' FROM 'TABLE NAME';

> 7.  SELECT DISTINCT 'COLUMN NAME' FROM 'TABLE NAME' LIMIT 10;

> 8.  SELECT DISTINCT 'COLUMN NAME' FROM 'TABLE NAME' LIMIT 10, 10;

> 9.  SELECT 'TABLE NAME'.'COLUMN NAME' FROM 'TABLE NAME';

> 10. SELECT 'COLUMN NAME' FROM 'TABLE NAME' ORDER BY NAME;

> 11. SELECT 'COLUMN NAME' FROM 'TABLE NAME' ORDER BY 'ORDER' LIMIT 1;

> 12. SELECT 'COLUMN NAME' FROM 'TABLE NAME' WHERE 'CONDITION';

> 13. SELECT 'COLUMN NAME' FROM 'TABLE NAME' WHERE 'CONDITION' BETWEEN 'CONDITION' AND 'CONDITION';

> 14. SELECT 'COLUMN NAME' FROM 'TABLE NAME' WHERE 'CONDITION' IN ('val1', 'val2');

> 15. SELECT NAME FROM ITEMS WHERE NAME LIKE '%new%'(% MEAN EVERYTHING);

> 16. SELECT NAME FROM items WHERE name LIKE '\_ BOXES OF FROGS';(\_ ONLY FOR SINGLE CHARACTER)

> 17. SELECT NAME FROM items WHERE name REGEXP 'NEW';

> 18. SELECT CONCAT(CITY, ', ', STATE) AS 'NEW COLUMN NAME' FROM cutomers;

> 19. SELECT NAME, COST, COST - 1 AS SALE_PRICE FROM items;

# Functions

CONCAT()

UPPER()

LOWER()

SQRT()

AVG()

SUM()

COUNT()

MAX()

MIN()

eg -> SELECT cost, SQRT(cost) FROM items;

> 20. SELECT COUNT(name) FROM items WHERE seller_id = 6;

> 21. SELECT seller_id, COUNT(\*) AS item_count FROM items GROUP BY seller_id;

> 22. SELECT seller_id, COUNT(\*) AS item_count FROM items GROUP BY seller_id HAVING COUNT(\*) >= 3;

# subqueries

query into another query.

> 1. SELECT name, cost FROM items WHERE cost > ( SELECT AVG(cost) FROM items ) ORDER BY cost DESC;

> 2. SELECT name, MIN(cost) FROM items WHERE name LIKE'%boxes of frogs' AND seller_id IN ( SELECT seller_id FROM items WHERE name LIKE '%boxes of frogs' ) ORDER BY cost DESC;

NOTE -> QUERIES run from inside out.

# JOIN

> SELECT i.seller_id, i.name, c.id FROM customers AS c, items AS i WHERE i.seller_id = c.id;

> SELECT customers.id , customers.name, items.name, items.cost FROM customers, items WHERE customers.id = seller_id ORDER BY customers.id;

> SELECT customers.name, items.name FROM customers LEFT OUTER JOIN items ON customers.id = seller_id;

> SELECT customers.name, items.name FROM customers RIGHT OUTER JOIN items ON customers.id = seller_id;

> SELECT customers.name, items.name FROM customers JOIN items ON customers.id = seller_id;

# UINON

> SELECT name, cost, bids FROM items WHERE bids > 190 UNION SELECT name, cost, bids FROM items WHERE cost > 1000;

> ALTER TABLE items ADD FULLTEXT(name)

> SELECT name, cost FROM items WHERE MATCH(name) Against ('baby');

> SELECT name, cost FROM items WHERE MATCH(name) Against('+baby -coat' IN BOOLEAN MODE);

> INSERT INTO items VALUES('v1', 'v2','v3','v4','v5');

> INSERT INTO items(id,name,cost,seller_id,bids) VALUES('104', '','9.95','1','0'), ('105','','93','2','0');

> UPDATE items SET name = 'puddin' WHERE id = 104;

> DELETE FROM items WHERE id = 104;

> CREATE TABLE users(id int AUTO_INCREMENT, username varchar(30) NOT NULL, password varchar(20), PRIMARY KEY(id));

> CREATE TABLE bacon(id int NOT NULL AUTO_INCREMENT,PRIMARY KEY(id));

> ALTER TABLE bacon ADD samplecolumn varchar(10);

> ALTER TABLE bacon DROP COLUMN samplecolumn;

> DROP TABLE bacon;

> RENAME TABLE bacon TO new_bacon;

# VIEW

> CREATE VIEW mostbids AS SELECT id, name, bids FROM items ORDER BY bids DESC LIMIT 10;

> CREATE VIEW city_state AS SELECT Concat(city,',',state) AS Address FROM customers LIMIT 10;

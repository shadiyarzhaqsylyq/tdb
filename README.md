## Educational database in C.





1 file 1 table


Flexible Primary Key - user_id INT PRIMARY KEY or product_code INT PRIMARY KEY

Types


VARCHAR(N), STRING(N), CHAR(N), INT, INTEGER


VARCHAR, CHAR - default 32


Operators - >=, <=, =, <, >, !=, <>

!= and <> have the same meaning "not equal to".
```
*CREATE*
CREATE TABLE emp (id INT PRIMARY KEY, name VARCHAR, did VARCHAR, dep VARCHAR, salary INT, city VARCHAR);
CREATE TABLE books (id INT PRIMARY KEY, title VARCHAR, isbn VARCHAR, genre VARCHAR, price INT, author VARCHAR);


*INSERT*
INSERT INTO emp VALUES (1, 'Alice', '1010A-1001a', 'Engineering', 12000, 'NY');
INSERT INTO emp VALUES (2, 'Bob', '1010A-1001b', 'IT', 18500, 'LA');
INSERT INTO emp VALUES (3, 'Charlie', '2020B-2001a', 'HR', 4000, 'SF');
INSERT INTO emp VALUES (4, 'Diana', '2020B-2001b', 'Finance', 21000, 'LA');
INSERT INTO emp VALUES (5, 'Evan', '3030C-3001a', 'HR', 3500, 'SF');
INSERT INTO emp VALUES (6, 'Frank', '3030C-3001b', 'HR', 11000, 'NY');

INSERT INTO books VALUES (1, 'The Great Gatsby', '978-0743273565', 'Fiction', 15, 'F. Scott Fitzgerald');
INSERT INTO books VALUES (2, 'To Kill a Mockingbird', '978-0061120084', 'Fiction', 18, 'Harper Lee');
INSERT INTO books VALUES (3, '1984', '978-0451524935', 'Dystopian', 12, 'George Orwell');
INSERT INTO books VALUES (4, 'Designing Data-Intensive Applications', '978-1449373320', 'Technology', 45, 'Martin Kleppmann');
INSERT INTO books VALUES (5, 'Clean Code', '978-0132350884', 'Technology', 40, 'Robert C. Martin');
INSERT INTO books VALUES (6, 'Dune', '978-0441172719', 'Sci-Fi', 22, 'Frank Herbert');



*SELECT*
SELECT * FROM table;
SELECT * FROM table WHERE a = '';
SELECT * FROM table WHERE a = '' AND b > '';
SELECT * FROM table WHERE a = '' OR b = '';
SELECT * FROM table WHERE (a = '' AND b = '') OR c < '';
SELECT * FROM table WHERE a = '' AND (b = '' OR d = '');


### Examples for SELECT
SELECT * FROM emp;
(1, 'Alice', '1010A-1001a', 'Engineering', 12000, 'NY')
(2, 'Bob', '1010A-1001b', 'IT', 18500, 'LA')
(3, 'Charlie', '2020B-2001a', 'HR', 4000, 'SF')
(4, 'Diana', '2020B-2001b', 'Finance', 21000, 'LA')
(5, 'Evan', '3030C-3001a', 'HR', 3500, 'SF')
(6, 'Frank', '3030C-3001b', 'HR', 11000, 'NY')


SELECT * FROM emp WHERE id = 1;
(1, 'Alice', '1010A-1001a', 'Engineering', 12000, 'NY')

SELECT * FROM emp WHERE city = 'NY' AND salary > 10000;
(1, 'Alice', '1010A-1001a', 'Engineering', 12000, 'NY')
(6, 'Frank', '3030C-3001b', 'HR', 11000, 'NY')

SELECT * FROM emp WHERE dep = 'HR' OR city = 'LA';
(2, 'Bob', '1010A-1001b', 'IT', 18500, 'LA')
(3, 'Charlie', '2020B-2001a', 'HR', 4000, 'SF')
(4, 'Diana', '2020B-2001b', 'Finance', 21000, 'LA')
(5, 'Evan', '3030C-3001a', 'HR', 3500, 'SF')
(6, 'Frank', '3030C-3001b', 'HR', 11000, 'NY')

SELECT * FROM emp WHERE (city = 'SF' AND dep = 'HR') OR id < 3;
(1, 'Alice', '1010A-1001a', 'Engineering', 12000, 'NY')
(2, 'Bob', '1010A-1001b', 'IT', 18500, 'LA')
(3, 'Charlie', '2020B-2001a', 'HR', 4000, 'SF')
(5, 'Evan', '3030C-3001a', 'HR', 3500, 'SF')

SELECT * FROM emp WHERE dep = 'HR' AND (city = 'SF' OR d = 'NY');
(5, 'Evan', '3030C-3001a', 'HR', 3500, 'SF')
(6, 'Frank', '3030C-3001b', 'HR', 11000, 'NY')


*UPDATE*
UPDATE table SET a = '' WHERE b = '';
UPDATE table SET a = '', b = '' WHERE c >= '';
UPDATE table SET a = '' WHERE b <= '' AND (c = '' OR d = '');

### Examples for UPDATE
UPDATE emp SET a = 'SF' WHERE id = 1;
(1, 'Alice', '1010A-1001a', 'Engineering', 12000, 'SF')
(2, 'Bob', '1010A-1001b', 'IT', 18500, 'LA')
(3, 'Charlie', '2020B-2001a', 'HR', 4000, 'SF')
(4, 'Diana', '2020B-2001b', 'Finance', 21000, 'LA')
(5, 'Evan', 'XXX', 'HR', 3500, 'Miami')
(6, 'Frank', 'XXX', 'HR', 11000, 'Miami')


UPDATE emp SET did = 'XXX', city = 'Miami' WHERE id >= 5;
(1, 'Alice', '1010A-1001a', 'Engineering', 12000, 'SF')
(2, 'Bob', '1010A-1001b', 'IT', 18500, 'LA')
(3, 'Charlie', '2020B-2001a', 'HR', 4000, 'SF')
(4, 'Diana', '2020B-2001b', 'Finance', 21000, 'LA')
(5, 'Evan', 'XXX', 'HR', 3500, 'Miami')
(6, 'Frank', 'XXX', 'HR', 11000, 'Miami')

UPDATE emp SET salary = 1 WHERE id <= 5 AND (city = 'LA' OR city = 'SF');
(1, 'Alice', '1010A-1001a', 'Engineering', 1, 'SF')
(2, 'Bob', '1010A-1001b', 'IT', 1, 'LA')
(3, 'Charlie', '2020B-2001a', 'HR', 1, 'SF')
(4, 'Diana', '2020B-2001b', 'Finance', 1, 'LA')
(5, 'Evan', 'XXX', 'HR', 3500, 'Miami')
(6, 'Frank', 'XXX', 'HR', 11000, 'Miami')


*DELETE*
DELETE FROM table WHERE a > '';
DELETE FROM table WHERE a < '';


DELETE FROM table WHERE a = '' OR b = '';
DELETE FROM table WHERE a = '' AND b = '';
DELETE FROM table WHERE (a = '' AND b = '') OR c <= '';
DELETE FROM table WHERE a > '' AND (b = '' OR c = '');

dbv2.c
DROP TABLE <name>;
ALTER TABLE <name> ADD [Column] <col> int|VARCHAR(n);
ALTER TABLE <name> DROP [Column] <col>;
ALTER TABLE <name> RENAME TO <new name>;
ALTER TABLE <name> RENAME COLUMN <old> TO <new>;
SELECT COUNT(*) FROM <name> WHERE <expr>

dbv3.c
SELECT * FROM emp ORDER BY salary; --ORDER BY uses ASC by default
SELECT * FROM emp ORDER BY salary DESC; --ASC/DESC dont work without ORDER BY.
SELECT * FROM emp ORDER BY name;   -- works on VARCHAR too


*LIMIT/OFFSET* Composable with ORDER BY, WHERE
SELECT * FROM emp LIMIT 2; --returns first 2 rows
SELECT * FROM emp OFFSET 2; --skips first 2 rows and returns next rows
SELECT * FROM emp ORDER BY id LIMIT 4;
SELECT * FROM emp ORDER BY id DESC LIMIT 2;
SELECT * FROM emp ORDER BY id DESC LIMIT 4 OFFSET 2; --skips 1 row returns 2 next rows

SELECT COUNT(*) FROM emp WHERE dept = 'eng';
SELECT SUM(salary) FROM emp;
SELECT AVG(salary) FROM emp WHERE dept = 'eng';
SELECT MIN(salary) FROM emp;
SELECT MAX(salary) FROM emp WHERE dept = 'sales';

gcc -Wall -Wextra db.c -o db

\q - exit,\? - for help

./db db.sql
./db sql
```





Not Implemented - Buffer Pool Manager, WAL/Recovery, Catalog, LRU-K replacer, Disk Scheduler, Disk Manager, query optimizer, executor, No free-page list, database wide transactions, Joins, foreign keys, USE statement



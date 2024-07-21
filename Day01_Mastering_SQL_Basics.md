1. PRIMARY KEY(by default NOT NULL and UNIQUE)
    varName DATATYPE PRIMARY KEY --> when we want single column as primary key
    or PRIMARY KEY (firstName, LastName)  --> when we want mix of multiple column as primary key, individual can be same but mix of firstName and lastName can't be same in the entire database.

2. NOT NULL: this column should not be NULL at any cost

3. DISCRIBE or DISC tableName(): want to know all the properties of columns, use DISCRIBE OR DISC, it will show you 
    what constraint table do has.

4. INSERT INTO tableName VALUES (values) (when you want to insert data as defined table col name)
   INSERT INTO tableName (col1, col2, col3) VALUES (provide values here with common) ==> if you don't want to insert in all col at same time or in same order

5. AUTO_INCREMENT: in case you want to start something from 1 or want know that will always increase by 1 then use 
    AUTO_INCREMENT, because it will add each time by 1, counting from previous one. BUTTTT use it carefully because if you set your primary key as autoIncrement, then your differentiating factor has been changed

6. WHERE: 
    we can addd conditions as many as we want...
```sql
SELECT * FROM employee WHERE salary >= 1000000 && firstName = "Ashish";
```
7. UPDATE(DML): used to update the data inside of the table
```SQL
UPDATE table_name
SET column1 = value1, column2 = value2, ...
WHERE condition;
```

8. ALTER(DDL): used to update schema of the table

9. DELETE(DML): it is used to delete a row from the given table, but when you don't give where clause, it will complete table's data only not schema
```SQL
DELETE FROM table_name WHERE condition;
17	Ayush	Raj	1000000	34	22
18	Ashish	Shah	34000	18	24
19	Ayush	Topper	4200140	14	27
20	Vijay	Ganesh	540004	54	12
21	Divyanshu	Chutiya	214000	87	25
22	Abhay	Sharma	2404400	32	7
23	Deepak	Sharma	100002	32	7					
```
it is giving me from 17 because i've deleted all the previous data and now auto_increment will count from next

10. SQL_SAFE_UPDATES = 1; when you try to perform delete or update without using where clause, it will give you warning that you can't do that because you're using safe mode, if you turn 0, then you're no longer will be in safe mode, so 


```SQL
SHOW DATABASES;

CREATE DATABASE IF NOT EXISTS techwithashish; -- NOW IT WILL WARNING
USE techwithashish;

DROP DATABASE TECHWITHASHISH;
SELECT DATABASE();

CREATE TABLE employee(
	empId INT AUTO_INCREMENT,
    firstName VARCHAR(20) NOT NULL,
    lastName VARCHAR(20) NOT NULL,
    salary INT NOT NULL DEFAULT 100000,
    age INT NOT NULL,
    startDate INT NOT NULL,
	PRIMARY KEY (empId) 
);

-- INSERT INTO employee VALUES (1, "Ashish", "Shah", 10, 21, 13);
-- INSERT INTO employee VALUES (2,"abhay", "Sharma", 10, 21, 13);
-- INSERT INTO employee VALUES (3, "Deepak", "Sharma", 10, 21, 13);
INSERT INTO employee (firstName, lastName, salary, age, startDate) VALUES ("Ayush", "Raj", 1000000, 34, 22);
INSERT INTO employee (firstName, lastName, salary, age, startDate) VALUES ("Ashish", "Shah", 34000, 18, 24);
INSERT INTO employee (firstName, lastName, salary, age, startDate) VALUES ("Ayush", "Topper", 4200140, 14, 27);
INSERT INTO employee (firstName, lastName, salary, age, startDate) VALUES ("Vijay", "Ganesh", 540004, 54, 12);
INSERT INTO employee (firstName, lastName, salary, age, startDate) VALUES ("Divyanshu", "Chutiya", 214000, 87, 25);
INSERT INTO employee (firstName, lastName, salary, age, startDate) VALUES ("Abhay", "Sharma", 2404400, 32, 7);
INSERT INTO employee (firstName, lastName, salary, age, startDate) VALUES ("Deepak", "Sharma", 100002, 32, 7);

-- INSERT INTO employee (firstName, lastName, age, startDate) VALUES ("Ashish", "Shah", 34, 22);

SELECT FIRSTNAME FROM EMPLOYEE;
 
-- give me the name of employee who's having salary more than 1 lakh
SELECT * FROM employee WHERE salary >= 1000000 || firstName = "Ashish";
-- give me the report of employees who's having age more than 25: this is the part of data retrival
SELECT * FROM employee WHERE age > 25;

SET SQL_SAFE_UPDATES = 1;
-- now it's time for updation part
-- update the last name of ashish with shah to shahu
UPDATE employee SET lastName = "ShahShah" where empId = 2;
UPDATE employee SET lastName = "Sharma" where empId = 1;
UPDATE employee SET lastName = "Shah" where firstName = 'Ayush';
DELETE FROM employee;
DELETE FROM employee where empId = 2;
SELECT * FROM employee;
DESC employee;
SHOW TABLES;
DROP TABLE employee;
```
CREATE SCHEMA schema1;
CREATE TABLE schema1.Person(
PersonID int,
FirstName VARCHAR(255),
LastName VARCHAR(255)
);
CREATE  TABLE schema1.Address(
AddressID int,
PersonID int,
City VARCHAR(255),
State VARCHAR(255)
);

INSERT INTO Person(PersonID, FirstName, LastName)
VALUES (1, 'Wang', 'Alen');

SELECT p.firstName, p.lastName, a.city, a.state FROM Person p
left join Address a
on p.personId=a.personId;

CREATE SCHEMA schema2;
CREATE TABLE If Not Exists Employee(
Id int,
Salary int
);

INSERT INTO employee(Id, Salary)
VALUES ('1', '100');

INSERT INTO employee(Id, Salary)
VALUES ('2', '200');

INSERT INTO employee(Id, Salary)
VALUES ('3', '300');

SELECT MAX(salary) from employee WHERE salary<(SELECT MAX(SALARY) FROM employee);

CREATE SCHEMA schema3;
CREATE TABLE Employee( Id int, n_ame VARCHAR (255), Salary int, ManagerId int );

INSERT INTO employee(Id, n_ame, Salary, MAnagerId) VALUES
(1,'Joe', 7000, 3),
(2,'Henry', 8000, 4);

INSERT INTO employee(Id, n_ame, Salary) VALUES
(3,'Sam', 6000),
(4,'Max', 9000);

SELECT e1.n_ame as Employee
FROM Employee as e1
LEFT JOIN Employee as e2
ON e1.ManagerId=e2.Id
WHERE e1.Salary>e2.Salary;

SELECT e1.n_ame AS Employee
FROM Employee e1 LEFT JOIN Employee e2
ON e1.ManagerId=e2.Id
WHERE e1.salary>e2.salary;

CREATE SCHEMA schema4;
Create table If Not Exists Person (Id int, Email varchar(255))
Truncate table Person
insert into Person (Id, Email) values ('1', 'a@b.com')
insert into Person (Id, Email) values ('2', 'c@d.com')
insert into Person (Id, Email) values ('3', 'a@b.com')

SELECT Email FROM Person
GROUP BY Email
HAVING COUNT(Email)>1;

SELECT DISTINCT a.Email
FROM Person a
JOIN Person b ON a.Email = b. Email
WHERE a.Id != b.Id

CREATE SCHEMA schema5;
Create table If Not Exists Customers (Id int, n_ame varchar(255))
Create table If Not Exists Orders (Id int, CustomerId int)
Truncate table Customers
insert into Customers (Id, n_ame) values ('1', 'Joe')
insert into Customers (Id, n_ame) values ('2', 'Henry')
insert into Customers (Id, n_ame) values ('3', 'Sam')
insert into Customers (Id, n_ame) values ('4', 'Max')
Truncate table Orders
insert into Orders (Id, CustomerId) values ('1', '3')
insert into Orders (Id, CustomerId) values ('2', '1')

SELECT c.n_ame as Customers
FROM Customers c
WHERE c.id not in (
SELECT o.CustomerId FROM Orders o
);


select Name Customers from Customers left join Orders on Orders.CustomerId=Customers.Id where Orders.Id is Null

CREATE SCHEMA schema6;

Create table If Not Exists courses (student varchar(255), class varchar(255))
Truncate table courses
insert into courses (student, class) values ('A', 'Math')
insert into courses (student, class) values ('B', 'English')
insert into courses (student, class) values ('C', 'Math')
insert into courses (student, class) values ('D', 'Biology')
insert into courses (student, class) values ('E', 'Math')
insert into courses (student, class) values ('F', 'Computer')
insert into courses (student, class) values ('G', 'Math')
insert into courses (student, class) values ('H', 'Math')
insert into courses (student, class) values ('I', 'Math')


SELECT class FROM courses GROUP BY class HAVING count (distinct student) >=5;
# Joins-and-Union
SQL Commands
Questions : 

6-Joins and Union
Consider the Country table and Persons table that you created earlier and perform the following:
 (1)Perform inner join, Left join, and Right join on the tables. 
(2)List all distinct country names from both the Country and Persons tables. 
(3)List all country names from both the Country and Persons tables, including duplicates. 
(4)Round the ratings of all persons to the nearest integer in the Persons table.

Create database Country_And_Polulation;
use  Country_And_Polulation;
--  Create a table named Country with fields: Id, Country_name, Population_Area 

create table Country ( ID int primary Key, Country_name varchar(20) not null, Population int ,Area int );
-- Create another table named Persons with fields: Id Fname Lname Population Rating Country_Id Country_name

Create Table Persons ( ID int , F_name varchar (20) not null ,  Lname varchar (20) , Population int , Rating dec,  Country_Id int ,Country_name varchar (20), foreign key (Country_Id) references Country(ID));

insert into Country(ID, Country_name,Population,Area) values 

(1,'India',1420000000,3287000),
(2,'USA',331000000,9834000),
(3,'UAE',83200000,357022),
(4,'Oman',25600000,3287000),
(5,'Lanka',1428700000,987000),
(6,'China',1444216107,9597000),
(7,'Canada',38000000,9985000),
(8,'Japan',213000000,377975),
(9,'Brazil',67000000,8516000),
(10,'UK',67000000,243610);

insert into Persons ( ID , F_name ,  Lname, Population, Rating,  Country_Id ,Country_name) values
(1,'Sharon','Pindi',331000000, 4,2,'India'),
(2,'Karthika','Nelath',38765890, 5,3,'USA'),
(3,'Giri','Krishna',331000000, 5,5,'UAE'),
(15,'Surya','Kumar',35640000, 3,7,'Oman'),
(5,'Sam','John',331087000, 9,6,'Lanka'),
(6,'Hari','Murali',201000000, 4,2,'China'),
(7,'Prathap','Chandra',101000000, 3,7,'Canada'),
(13,'Manu','Manohar',671000000, 4,8,'Australia'),
(9,'Sree','Kala',381000000, 3,10,'Brazil'),
(12,'Krish','Lol',121000000, 5,1,'UK');

--  (1)Perform inner join, Left join, and Right join on the tables.

-- inner join
select P.ID, P.F_name,P.Lname, P.Country_Name , C.ID from Persons P
inner join Country C on P.ID = C.ID;

-- Left join

select P.ID, P.F_name,P.Lname, P.Country_Name , C.ID from Persons P
Left join Country C on P.ID = C.ID;

-- Right join
select P.ID, P.F_name,P.Lname, P.Country_Name , C.ID from Persons P
Right join Country C on P.ID = C.ID;


-- List all distinct country names from both the Country and Persons tables

select distinct Country_name as name from country
union
select distinct  Country_name as name from Persons;

-- (3)List all country names from both the Country and Persons tables, including duplicates.

select  Country_name as name from country
union all
select  Country_name as name from Persons;

-- (4)Round the ratings of all persons to the nearest integer in the Persons table.

select Rating, round(Rating,0) as Rounded_Rating from Persons;

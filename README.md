# Banking-database
create table Customer
(
	Customer_ID int IDENTITY(7000,1) PRIMARY KEY,
	Title varchar(30) NOT NULL,
	First_name varchar(30) NOT NULL,
	Middle_Name varchar(30),
	Last_Name varchar(30) NOT NULL,
	Father_Name varchar(30) NOT NULL,
	Mobile_Number varchar(30)	NOT NULL,
	Email_Id varchar(30) NOT NULL,
	Address_Line1 varchar(30) NOT NULL,
	Address_Line2 varchar(30),
	Landmark varchar(30),  
	[State] varchar(30) NOT NULL,
	City varchar(30) NOT NULL,
	pincode varchar(30) NOT  NULL,
	Aadhar_NUMBER varchar(12) NOT NULL,
	Occupation_type varchar(30) not null,
	Source_of_income varchar(30) not null,
	Gross_annual_income varchar(30) not null,
)
select * from Customer
create table Account
(
	Account_Number int IDENTITY(10000,1) PRIMARY KEY,
	Balance int default  0,
	Account_type varchar(30)  default 'Savings',
	Customer_ID int FOREIGN KEY references Customer(Customer_ID)
)
select * from Account
create table InternetBanking
(
	Internet_Banking_ID int IDENTITY(5000,1) PRIMARY KEY,
	Customer_ID int FOREIGN KEY references Customer(Customer_ID),
	Transaction_password varchar(30) not null,
	Account_Number int FOREIGN KEY references Account(Account_Number),	
)

select * from InternetBanking

create table Beneficiary
(
	Beneficiary_name  varchar(30) not null,
	Beneficiary_account_no int FOREIGN KEY references Account(Account_Number),
	Nick_name  varchar(30),
	Account_Number int Foreign Key references Account(Account_Number),
	CONSTRAINT PK_Beneficiary_accountNo PRIMARY KEY (Account_Number,Beneficiary_account_no),	
)
delete from Beneficiary where Beneficiary_name='Vijay'
select * from Beneficiary
delete from Beneficiary
create table Transactions
(
	Transaction_id  int IDENTITY(2000,1) primary key,
	From_AccountNo  int FOREIGN KEY references Account(Account_Number),
	To_AccountNo  int FOREIGN KEY references Account(Account_Number),
	Amount int not null,
	Mode varchar(30) not null,
	Date varchar(30) not null,
	Time varchar(30) not null,
)
select * from Transactions
delete from Transactions where Transaction_id=2000
create table Register
(
 Register_ID int IDENTITY(4000,1) primary key,
 Customer_ID int FOREIGN KEY references Customer(Customer_ID),
 Password varchar(30) not null
)
select * from Register
drop table Customer
drop table Account
drop table Beneficiary
drop table InternetBanking
drop table Register
drop table Transactions

use Banking;

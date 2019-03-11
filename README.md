# AssigmentDB

# /1 
select customers.customerName, 
employees.firstName, 
customers.city
  FROM customers
 INNER JOIN employees ON employees.employeeNumber = customers.salesRepEmployeeNumber
 INNER JOIN offices ON offices.officeCode = employees.officeCode
 Where customers.city = offices.city

# /2

# /3
GROUPING
select offices.officeCode, SUM(payments.amount), max(payments.amount)
 From offices 
 Inner join employees on employees.officeCode = employees.officeCode
 inner join customers on customers.salesRepEmployeeNumber = employees.employeeNumber
 Inner Join payments on payments.customerNumber = customers.customerNumber
 group by officeCode;

WINDOWING
select offices.officeCode, 
SUM(payments.amount) OVER (partition by offices.officeCode) as SUM, 
max(payments.amount) OVER (partition by offices.officeCode) as Max
 From offices 
 Inner join employees on employees.officeCode = employees.officeCode
 inner join customers on customers.salesRepEmployeeNumber = employees.employeeNumber
 Inner Join payments on payments.customerNumber = customers.customerNumber

# /4
Wasn't able to import the dataset so I did something that reminds of this project in the the same data set.
 select customerName, country from customers where country like '%France%';

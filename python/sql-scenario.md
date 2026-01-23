# SQL Scenario

## Banking Domain Scenario

Consider a Banking system which has multiple services provided to the customers at national level. Create as many tables needed for the below entities and create needed columns for the different services provided by the Bank.

Types of services provided:

a. Account (Savings, Current)

b. Loan

c. Card services (Debit and Credit)

Consider all Savings accounts and Current accounts are associated with debit card services by default.

Loan services are provided only to the customers who are associated with the bank for 24 months.

Credit card services are provided only for the customer who has made 1,00,000 transactions within the last one year from the current date.

All type of service have the status active, inactive, closed.

Questions:

Create a Database which covers all the entities based on the understanding.

Create a normalized tables based on the needs.

Create a table with all key constraints.

Based on the table created above:

Generate a SQL query for eligible customers for the LOAN.

Generate a SQL query for eligible customers for the Credit card service.

Generate a SQL query for customers who did not do any transactions for the past 6 months.

Generate a SQL query where customers’ participation is less in particular location.

Generate a SQL query where customer and loan and outstanding amount.

Generate a SQL query with all details like Customer, account, type, Balance amount based on the transaction.

Generate a SQL query with loan details and history of payments done by the customer and outstanding amount to be paid.

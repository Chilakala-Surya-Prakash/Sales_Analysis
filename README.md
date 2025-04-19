## Sales Insights Data Analysis Project

### Instructions to setup mysql on your local computer

1. Follow step in this video to install mysql on your local computer
https://www.youtube.com/watch?v=WuBcTJnIuzo

1. SQL database dump is in db_dump.sql file above. Download `db_dump.sql` file to your local computer and import it as per instructions given in the tutorial video

### Data Analysis Using SQL

1. Show all customer records

    `SELECT * FROM customers;`

2. Show total number of customers

    `SELECT count(*) FROM customers;`

3. Show transactions for Chennai market (market code for chennai is Mark001

    `SELECT * FROM transactions where market_code='Mark001';`

4. Show distrinct product codes that were sold in chennai

    `SELECT distinct product_code FROM transactions where market_code='Mark001';`

5. Show transactions where currency is US dollars

    `SELECT * from transactions where currency="USD"`

6. Show transactions in 2020 join by date table

    `SELECT transactions.*, date.* FROM transactions INNER JOIN date ON transactions.order_date=date.date where date.year=2020;`

7. Show total revenue in year 2020,

    `SELECT SUM(transactions.sales_amount) FROM transactions INNER JOIN date ON transactions.order_date=date.date where date.year=2020 and transactions.currency="INR\r" or transactions.currency="USD\r";`
	
8. Show total revenue in year 2020, January Month,

    `SELECT SUM(transactions.sales_amount) FROM transactions INNER JOIN date ON transactions.order_date=date.date where date.year=2020 and and date.month_name="January" and (transactions.currency="INR\r" or transactions.currency="USD\r");`

9. Show total revenue in year 2020 in Chennai

    `SELECT SUM(transactions.sales_amount) FROM transactions INNER JOIN date ON transactions.order_date=date.date where date.year=2020
and transactions.market_code="Mark001";`

10.-- To INNER JOIN  transactions and date 

SELECT sales.transactions.* , sales.date.*
FROM sales.transactions INNER JOIN sales.date 
ON sales.transactions.order_date = sales.date.date;

11.-- To INNER JOIN based on year

SELECT sales.transactions.* , sales.date.*
FROM sales.transactions INNER JOIN sales.date 
ON sales.transactions.order_date = sales.date.date
WHERE sales.date.year = 2020;


12-- To get the total revenue in a year and in  a state based on market code

SELECT SUM(sales.transactions.sales_amount) 
FROM sales.transactions INNER JOIN sales.date 
ON sales.transactions.order_date = sales.date.date
WHERE sales.date.year = 2020 and sales.transactions.market_code = "Mark001";

13.-- list of  disctinct products that you sold in chennai/market_code = Mark001

SELECT distinct product_code FROM sales.transactions WHERE market_code = "Mark001";

14-- to find the revenue wrt year

SELECT SUM(sales.transactions.sales_amount) 
FROM sales.transactions INNER JOIN sales.date 
ON sales.transactions.order_date = sales.date.date
WHERE sales.date.year = 2020 and transactions.currency = "INR\r" or transactions.currency = "USD\r";







PowerBI-Project-- **Sales Insights Data Analysis Project**
This project is based on a computer hardware business which is facing challenges in dynamically changing market. Sales director decides to invest in data analysis project and he would like to build power BI dashboard that can give him real time sales insights. 
mysql database  is owned by the falcons team. This database has all sales transactions, customers, products, and market information.
**Taskes performed:**
1. Analysing the database and then hook it up with power BI.
2. In power BI  performing ETL and data cleaning operations to make it ready so that we can build our dashboard.
3. More data cleaning and building a powerful dashboard that can help us generate sales insights on the Atliq hardware business.
4. Data visualization techniques to uncover actionable insights for strategic decision-making.
5. SQL database dump is in db_dump.sql file . Downloading db_dump.sql file rand importing it.
The key analyses conducted in this project include:
**Data Analysis Using SQL**
1.Show all customer records:
SELECT * FROM customers;

2.Show total number of customers:
SELECT count(*) FROM customers;

3.Show transactions for Chennai market (market code for chennai is Mark001:
SELECT * FROM transactions where market_code='Mark001';

4.Show distrinct product codes that were sold in chennai:
SELECT distinct product_code FROM transactions where market_code='Mark001';

5.Show transactions where currency is US dollars:
SELECT * from transactions where currency="USD"

6.Show transactions in 2020 join by date table:
SELECT transactions.*, date.* FROM transactions INNER JOIN date ON transactions.order_date=date.date where date.year=2020;

7.Show total revenue in year 2020:
SELECT SUM(transactions.sales_amount) FROM transactions INNER JOIN date ON transactions.order_date=date.date where date.year=2020 and transactions.currency="INR\r" or transactions.currency="USD\r";

8.Show total revenue in year 2020, January Month:
SELECT SUM(transactions.sales_amount) FROM transactions INNER JOIN date ON transactions.order_date=date.date where date.year=2020 and and date.month_name="January" and (transactions.currency="INR\r" or transactions.currency="USD\r");

9.Show total revenue in year 2020 in Chennai:
SELECT SUM(transactions.sales_amount) FROM transactions INNER JOIN date ON transactions.order_date=date.date where date.year=2020 and transactions.market_code="Mark001";

**Data Analysis Using Power BI**
Formula to create norm_amount column
= Table.AddColumn(#"Filtered Rows", "norm_amount", each if [currency] = "USD" or [currency] ="USD#(cr)" then [sales_amount]*75 else [sales_amount], type any)

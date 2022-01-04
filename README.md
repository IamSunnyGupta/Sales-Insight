# Sales-Insight
## This is a portfolio project i made with a datasets of a computer hardware company. <br />
### **Problem Statement** - Computer Hardware manufacturer is facing issues in terms of their sales. <br/> <br/>

I've done the data analysis and data cleaning in SQL and made a dashboard in Microsoft PowerBI. <br/>
PowerBI dashboard where stakeholders can- <br/>
1. Track revenue numbers <br/>
2. Track sales quantity number year over year. <br/>
3. Revenue breakdown by regions and by products. <br/>
4. Track the revenue trends. <br/>
### Final Dashboard in PowerBI
![](https://github.com/IamSunnyGupta/Sales-Insight/blob/main/Final%20Dashboard_page-0001.jpg)

### Data Analysis Using SQL



1. To Show total number of customers

    `SELECT count(*) FROM customers;`

1. To Show transactions for Chennai market (market code for chennai is Mark001

    `SELECT * FROM transactions where market_code='Mark001';`

1. To Show distinct product codes that were sold in chennai

    `SELECT distinct product_code FROM transactions where market_code='Mark001';`

1. To Show transactions where currency is US dollars

    `SELECT * from transactions where currency="USD"`

1. To Show transactions in 2020 join by date table

    `SELECT transactions.*, date.* FROM transactions INNER JOIN date ON transactions.order_date=date.date where date.year=2020;`

1. To Show total revenue in year 2020,

    `SELECT SUM(transactions.sales_amount) FROM transactions INNER JOIN date ON transactions.order_date=date.date where date.year=2020 and transactions.currency="INR\r" or transactions.currency="USD\r";`
	
1. To Show total revenue in year 2020, January Month,

    `SELECT SUM(transactions.sales_amount) FROM transactions INNER JOIN date ON transactions.order_date=date.date where date.year=2020 and and date.month_name="January" and (transactions.currency="INR\r" or transactions.currency="USD\r");`

1. To Show total revenue in year 2020 in Chennai

    `SELECT SUM(transactions.sales_amount) FROM transactions INNER JOIN date ON transactions.order_date=date.date where date.year=2020
and transactions.market_code="Mark001";`


Data Analysis Using Power BI
============================

1. Formula to create norm_amount column

`= Table.AddColumn(#"Filtered Rows", "norm_amount", each if [currency] = "USD" or [currency] ="USD#(cr)" then [sales_amount]*75 else [sales_amount], type any)`




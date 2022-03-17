# sales_Insight

## Data Exploratory analysis with SQL

#### 1. Show all Customer and Transaction records
###### SELECT * FROM sales.customer;

###### SELECT * FROM sales.transactions;

#### 2. Show total customers
###### SELECT count(*) FROM sales.customers;

#### 3. Show transactions for Chennai market (market code for Chennai is Mark001)
###### SELECT * FROM sales.transactions
WHERE market_code = 'mark001';

#### 4. Show distinct product codes that were sold in Chennai
###### SELECT distinct(product_code) FROM sales.transactions
where market_code = 'mark001';

#### 5. Show transactions where the currency is US dollars
SELECT * from transactions where currency="USD"

#### 6. Show transactions in 2020 join by date table
###### SELECT * from transactions as t
inner join date as d on t.order_date = d.date
where year = 2020;

#### 7. Show total revenue in the year 2020,
###### SELECT sum(sales_amount) from transactions as t
inner join date as d on t.order_date = d.date
where d.year=2020 and t.currency="INR\r" or t.currency="USD\r";

#### 8. Show total revenue in year 2020, January Month,
###### SELECT sum(sales_amount) from transactions as t
inner join date as d on t.order_date = d.date
where d.year=2020 and d.month_name = 'january' and (t.currency="INR\r" or
t.currency="USD\r");

#### 9. Show total revenue in year 2020 in Chennai
###### SELECT sum(sales_amount) from transactions as t
inner join date as d on t.order_date = d.date
where d.year=2020 and market_code = 'mark001' and (t.currency="INR\r" or
t.currency="USD\r");

#### 10. Show total sales by year
###### SELECT year,sum(sales_amount) from transactions as t
inner join date as d on t.order_date = d.date
where t.currency="INR\r" or t.currency="USD\r"
group by year;

#### 11. Show top product
###### SELECT product_code ,sum(sales_amount) as top_product from
transactions as t
group by product_code
order by top_product desc;

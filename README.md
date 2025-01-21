# Pizza-Sales-Report  
Power BI 

# [Project 1: Pizza-Sales-Report](https://akedataanalyst.github.io/Pizza-Sales-Report/)

This project focuses on  visualizing various aspects of pizza sales data to gain insights and understand key trends

[Excel Pizza Sales file](pizza_sales_excel_file.xlsx)

## Daily trends for total orders 

`select DATENAME(DW,order_date) as order_day, count(distinct order_id) as total_orders 
from pizza_sales_excel_file
group by DATENAME(DW,order_date)`

## Monthly trend for total orders

`select datename(month,order_date) as month_name, count(distinct order_id) as total_orders
from pizza_sales_excel_file
group by datename(month,order_date)
order by total_orders desc`

## percentage of sales by pizza catagory

`select pizza_category, sum(total_price)*100/(select sum(total_price) from pizza_sales)`

`select pizza_category,sum(total_price) as total_sales, sum(total_price) * 100 / (select sum(total_price) 
from  pizza_sales_excel_file where month(order_date) = 1 ) as pct
from pizza_sales_excel_file 
where month(order_date) = 1
group by pizza_category`

## percentage of sales by pizza size

`select pizza_size,cast(sum(total_price) as decimal(10,2)) as total_sales, cast(sum(total_price) * 100 / ( select sum(total_price) 
from  pizza_sales_excel_file where datepart(quarter,order_date)=1)  as decimal(10,2)) as pct
from pizza_sales_excel_file 
where datepart(quarter,order_date)=1
group by pizza_size
order by pct desc`

![](pizza0.PNG)

## top 5 best sellers by revenue,total quantity and total orders

`select top 5 pizza_name, sum(total_price) AS total_revenue from pizza_sales_excel_file
group by pizza_name 
order by total_revenue desc`

`select top 5 pizza_name, sum(quantity) AS total_quantity from pizza_sales_excel_file
group by pizza_name 
order by total_quantity desc`

`select top 5 pizza_name, count(distinct order_id) AS total_order from pizza_sales_excel_file
group by pizza_name 
order by total_order desc`

## bottom 5 best sellers by revenue,total quantity and total orders
`select top 5 pizza_name, sum(total_price) AS total_revenue from pizza_sales_excel_file
group by pizza_name 
order by total_revenue asc`


`select top 5 pizza_name, sum(quantity) AS total_quantity from pizza_sales_excel_file
group by pizza_name 
order by total_quantity asc`

![](pizza1.PNG)

# Thank You for Your Time!

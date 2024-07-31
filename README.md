# Pizza Sales Report-Dashboard

### Dashboard Link : (https://github.com/user-attachments/assets/446dd335-4f57-4396-817f-08bc7ecabf1b)

(https://github.com/user-attachments/assets/4e4e1fa5-7b5f-4b24-b205-ba6dd8168fa8)

## Problem Statement

This dashboard helps the Pizza Sales understand their customers better. It helps the Sales Report know if their customers are satisfied with their services. Through different ratings, they get to know their improvement area, & thus they can improve their services by identifying these area. It also lets them know the Average Order Values, Total Revenue, Total Pizza Sold, Total oeders and Average Pizza Per Orders, thus since by using this dashboard they have identified this report, they can further work on factors responsible for the Sales.

Since, number of Total Revenue($817.9k),Average Order Values(38.31),Total Pizza Sold(50K), Total orders(21k), Average Pizza For order(2.32)



### Steps followed 

- Step 1 : Create a New Database, Load data into Database, dataset is a csv file.

- Step 2 : Create a Table and write a Data query for Total Revenue

for Total Revenue following query was written

1. Total Revenue:
SELECT SUM(total_price) AS Total_Revenue FROM pizza_sales;

Snap_1 :

 ![total revenuye1](https://github.com/user-attachments/assets/2b392468-75e6-41be-bd8a-4dd57dedfd3a)

- Step 3 : Create a Table and write a Data query for  Average Order Value

2. Average Order Value
SELECT (SUM(total_price) / COUNT(DISTINCT order_id)) AS Avg_order_Value FROM pizza_sales

Snap_2 :

![avg order value](https://github.com/user-attachments/assets/38de14c5-03da-470c-a57d-60a529df0aea)

- Step 4 :Create a Table and write a Data query for  Total Pizzas Sold 

3. Total Pizzas Sold
SELECT SUM(quantity) AS Total_pizza_sold FROM pizza_sales

Snap_3

![total pizza sold](https://github.com/user-attachments/assets/2d15de33-ed38-43c0-9ccd-7e188db449af)

- Step 5 :Write a Data query for  Total orders

4. Total Orders
SELECT COUNT(DISTINCT order_id) AS Total_Orders FROM pizza_sales

snap_4

![total orders](https://github.com/user-attachments/assets/36864465-f6e9-4e40-b260-bfcd48855c56)

- Step 6 : Write a Data query for Average Pizzas Per Order  

5. Average Pizzas Per Order
SELECT CAST(CAST(SUM(quantity) AS DECIMAL(10,2)) / 
CAST(COUNT(DISTINCT order_id) AS DECIMAL(10,2)) AS DECIMAL(10,2))
AS Avg_Pizzas_per_order
FROM pizza_sales

snap 5

![avg pizza per](https://github.com/user-attachments/assets/4dc9856b-2c38-41f1-9d5e-ae8a3bd33ede)


B. Daily Trend for Total Orders

- Step 7 : Data query for Daily Trend for Total Orders

SELECT DATENAME(DW, order_date) AS order_day, COUNT(DISTINCT order_id) AS total_orders 
FROM pizza_sales
GROUP BY DATENAME(DW, order_date)

snap 6

![daily](https://github.com/user-attachments/assets/8bf75a61-ea8f-49aa-b1d6-cd84f2ab00dd)

- Step 8 : Data query for  Monthly Trend for Orders

select DATENAME(MONTH, order_date) as Month_Name, COUNT(DISTINCT order_id) as Total_Orders
from pizza_sales
GROUP BY DATENAME(MONTH, order_date)

snap 7

![month](https://github.com/user-attachments/assets/d21193ed-49d6-4742-938f-c77da6970ed4)

- Step 9 :  Data query for Pizza Category  

  % of Sales by Pizza Category

  snap 8

  
![pizza cat](https://github.com/user-attachments/assets/327c14d0-8657-46c6-bad3-385ebceff259)


- Step 10 : % of Sales by Pizza Size

SELECT pizza_size, CAST(SUM(total_price) AS DECIMAL(10,2)) as total_revenue,
CAST(SUM(total_price) * 100 / (SELECT SUM(total_price) from pizza_sales) AS DECIMAL(10,2)) AS PCT
FROM pizza_sales
GROUP BY pizza_size
ORDER BY pizza_size

snap 9

![pizza size](https://github.com/user-attachments/assets/0a2c4f96-e7cc-4e84-b409-c7953a894cee)

- Step 11 : Total Pizzas Sold by Pizza Category


SELECT pizza_category, SUM(quantity) as Total_Quantity_Sold
FROM pizza_sales
WHERE MONTH(order_date) = 2
GROUP BY pizza_category
ORDER BY Total_Quantity_Sold DESC

snap 10

![total pizza category](https://github.com/user-attachments/assets/8d9128ac-1f0e-42a5-badc-8e1b5d3e4505)

- Step 12 : Top 5 Pizzas by Revenue


SELECT Top 5 pizza_name, SUM(total_price) AS Total_Revenue
FROM pizza_sales
GROUP BY pizza_name
ORDER BY Total_Revenue DESC

snap 11

![top 55](https://github.com/user-attachments/assets/4c618bcb-3b79-4264-a2b4-314546e2d8b7)

- Step 13 : Bottom 5 Pizzas by Revenue

SELECT Top 5 pizza_name, SUM(total_price) AS Total_Revenue
FROM pizza_sales
GROUP BY pizza_name
ORDER BY Total_Revenue ASC

snap 12

![bottom 55](https://github.com/user-attachments/assets/13ae844d-0fa6-437c-99e1-6cb8573e8424)

- Step 14 : Top 5 Pizzas by Quantity

SELECT Top 5 pizza_name, SUM(quantity) AS Total_Pizza_Sold
FROM pizza_sales
GROUP BY pizza_name
ORDER BY Total_Pizza_Sold DESC

snap 13

![top 555](https://github.com/user-attachments/assets/7bb621ec-3eb0-4495-88d7-46125f50452f)

- Step 15 : Bottom 5 Pizzas by Quantity

SELECT TOP 5 pizza_name, SUM(quantity) AS Total_Pizza_Sold
FROM pizza_sales
GROUP BY pizza_name
ORDER BY Total_Pizza_Sold ASC

snap 14

![botom 555](https://github.com/user-attachments/assets/784a373c-b4a4-4f13-b05d-8d6da05aca28)

- Step 16 : Top 5 Pizzas by Total Orders

SELECT Top 5 pizza_name, COUNT(DISTINCT order_id) AS Total_Orders
FROM pizza_sales
GROUP BY pizza_name
ORDER BY Total_Orders DESC

snap 15

![top 5555](https://github.com/user-attachments/assets/7777e8b2-4575-4cbf-bccd-9b019036e6a1)

- Step 17 : Borrom 5 Pizzas by Total Orders

SELECT Top 5 pizza_name, COUNT(DISTINCT order_id) AS Total_Orders
FROM pizza_sales
GROUP BY pizza_name
ORDER BY Total_Orders ASC

snap 16


![bottom 5555](https://github.com/user-attachments/assets/3797b822-8c1f-4c4d-9676-fd54a6ea1f87)


### Steps followed 

-Step 18 : Now Load data into Power BI Desktop, dataset is a csv file and connect to mysql.

-Step 19 : New measure was created to Average Order Values.

Following DAX expression Average Order Values



Average Order Values = [TOTAL REVENUE]/[TOTAL ORDERS] Total Revenue, Total Pizza Sold, Total oeders and Average Pizza Per Orders.

-Step 20 : New measure was created to
Total Pizza Sold 


Following DAX expression Total Pizza Sold 



Total Pizza Sold = SUM( pizza sales[QUALITY])

-Step 21 : New measure was created to Total orders

Following DAX expression Total orders



TOTAL ORDERS = DISTINTCOUNT(pizza_sales[ORDER_ID])


-Step 22 : New measure was created to Avg Pizzas per order

Following DAX expression Avg Pizzas per order




Avg Pizzas per order = [TOTAL PIZZAS SOLD]/[TOTAL ORDERS]



-Step 23 =  Although, Add New Card Data Visualization drag the Data Average Order Values, Total Pizza Sold, Total orders Average Pizza Per Orders and Total Revenue and format the KPI's.


-Step 24 = A bar chart was also added to the report design area Order day/Total orders representing the Daily Trend for Total Orders.



-Step 25 = Area Chart was added to the report design Total Orders by order month area representing the Month_Name and total_orders.



-Step 26 = Donut Chart was added to the report design Pizza category/total revenue representing the % of sales by Pizza Categories.



-Step 27 = Donut Chart was added to the report design Pizza Size/total revenue representing the % of sales by Pizza Size.



-Step 28 = Funnel Chart was added to the report design Pizza Category/Total Pizza Sold representing the Total Pizza Sold by Pizza Categories



-Step 29 = Bar Chart was added to the report design Pizza Name/Total Revenue Sold representing the Top 5 Pizzas by Revenue and  Bottom 5 Pizzas by Revenue



-Step 30 = Bar Chart was added to the report design Pizza Name/  Total_Pizza_Sold representing the Top 5 Pizzas by Total Orders
  and Bottom 5 Pizzas by Total Orders

-Step 31 = Bar Chart was added to the report design Pizza Name/ Total_Pizza_Sold Sold representing the Top 5 Pizzas by Quantity 
  and  Bottom 5 Pizzas by Quantity


Step 32 : Ratings Visual was used to represent different ratings mentioned below,

 A. KPI’s

 B. Daily Trend for Total Orders

 C. Monthly Trend for Orders

 D. % of Sales by Pizza Category

 E. % of Sales by Pizza Size

 F. Total Pizzas Sold by Pizza Category

 G. Top 5 Pizzas by Revenue

 H. Bottom 5 Pizzas by Revenue

 I. Top 5 Pizzas by Quantity

 J. Bottom 5 Pizzas by Quantity

 K. Top 5 Pizzas by Total Orders

 L. Borrom 5 Pizzas by Total Orders

    
 

# Insights

A single page report was created on Power BI Desktop.

# Snapshot of Dashboard (Power BI DESTOP)

![Screenshot (54)](https://github.com/user-attachments/assets/446dd335-4f57-4396-817f-08bc7ecabf1b)






![Screenshot (55)](https://github.com/user-attachments/assets/4e4e1fa5-7b5f-4b24-b205-ba6dd8168fa8)







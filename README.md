# DSA-DATA-ANALYSIS-CAPSTONE-PROJECT-SQL-
This is my first project as a data analyst under DSA. I am not perfect, but I am learning and aiming to improve as I embark on this new journey.



```````SQL
select * from KMS
```

`````SQL
-----------1. Which Product Category Had The Highest Sales?
SELECT top 1 Product_Category, SUM(Sales) AS Total_Sales
FROM KMS
GROUP BY Product_Category
ORDER BY Total_Sales DESC
```

````````SQL
--------2a. What Are The Top 3  Region In Term Of Sales 
select top 3 REGION, SUM(Sales) AS Total_Sales
from KMS
GROUP BY REGION
order by TOTAL_SALES DESC
```

``````SQL
---------2b.What Are The Bottom 3  Region In Term Of Sales
select top 3 REGION, SUM(Sales) AS Total_Sales
from KMS
GROUP BY REGION
order by TOTAL_SALES asc
`````````-

`````````SQL
----------3. What were the total sales of appliance in Ontario?
select 'ontario' region, sum(sales) as appliance_sales
from KMS
WHERE PRODUCT_SUB_CATEGORY = 'APPLIANCES' 
AND Region = 'ONTARIO';
````````-

```````SQL
----------4. Advise the management of kms on what to do to increase the revenue from the bottom 10 customers
select top 10 Customer_name, SUM(sales) AS Total_sales
from KMS
GROUP BY Customer_name
order by TOTAL_sales asc
`````````-

````````SQL
---------5. KMS Incurred the most shipping cost using which shiping methos?
select ship_mode, SUM(shipping_cost) AS Total_shipping_cost
from KMS
GROUP BY ship_mode
order by Total_shipping_cost desc
```

``````````SQL
----------6. Who are the most valuable customers, and what products or services do they typically purchase?
select top 10 Customer_name, SUM(sales) AS Total_sales
from KMS
GROUP  BY Customer_name
order by TOTAL_sales desc
```

````````SQL
-------6b. what products or services do they typically purchase?

select top 10 * from (
      select customer_name, product_category
	        from KMS) as PURCHASE_COUNT 
```

``````SQL
select * from KMS
```

````````SQL
----------7. Which small business customers had the highest sales?
SELECT Customer_Name, SUM(Sales) AS Total_Sales
FROM kms
WHERE customer_Segment = 'Small Business'
GROUP BY Customer_Name
ORDER BY Total_Sales DESC
OFFSET 0 ROWS FETCH NEXT 1 ROWS ONLY;
```

````````SQL
----------8.Which corporate customer placed the most number of order in 2009-2012
SELECT top 1 Customer_Name, COUNT(Order_ID) AS Total_Orders
FROM kms
WHERE customer_Segment = 'Corporate'
AND Order_Date BETWEEN '2009-01-01' AND '2012-12-31'
GROUP BY Customer_Name
ORDER BY Total_Orders DESC;
```

``````SQL
-----------9. Which consumer customer was the most profitable one?
select top 1 Customer_Name, sum(profit) as total_profit
from kms
where customer_segment = 'consumer'
group by customer_name
order by total_profit desc;
```

```````SQL
-----------10. Which customer returned items, and what segment do they belong to?
select distinct 0.customer_name, 0.customer_segment
from kms k
join  kms on k.Order_id = k.order_id;
```

``````SQL
--------11. If the delivery truck is the most economical but the slowest shipping method and express air is the fastest but the most expensive one, do you think the company appropriately spent shipping costs based on the order priority? Explain your answer
SELECT 
    Order_Priority, 
    Ship_Mode, 
    COUNT(Order_ID) AS Total_Orders,
    SUM(Shipping_Cost) AS Total_Shipping_Cost,
    AVG(Shipping_Cost) AS Avg_Cost_Per_Order
FROM kms
GROUP BY Order_Priority, Ship_mode
ORDER BY Order_Priority, Ship_Mode;
```

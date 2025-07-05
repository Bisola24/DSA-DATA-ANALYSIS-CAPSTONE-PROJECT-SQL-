# DSA-DATA-ANALYSIS-CAPSTONE-PROJECT-SQL-
This is my first project as a data analyst under DSA. I am not perfect, but I am learning and aiming to improve as I embark on this new journey.

1.Which Product Category Had The Highest Sales?				

Product_Category	Total_Sales			
Technology	         5984248.175			
				
2A.What Are The Top 3  Region In Term Of Sales 				

Region	Total_sales			
West	3597549.27			
Ontario	3063212.476			
Prarie	2837304.605			
				
2B.What Are The Bottom 3  Region In Term Of Sales				

Region	               Total_sales			
Nunavut	                116376.4838			
Northwest Territories	800847.3309			
Yukon	                975867.3757			
				
3.What were the total sales of appliance in Ontario?				

Region	       appliance_sales			
Ontario	         202346.8396			
				
4.Advise the management of kms on what to do to increase the revenue from the bottom 10 customers				

Customer_name	                Total_sales			
Jeremy Farry	                 85.72000217			
Natalie DeCherney	         125.9000015			
Nicole Fjeld	                 153.0300064			
Katrina Edelman         	 180.760006			
Dorothy Dickinson	         198.0800018			
Christine Kargatis	         293.220005			
Eric Murdock	                 343.3279991			
Chris McAfee	                 350.1800041			
Rick Huthwaite	                 415.8199806			
Mark Hamilton	                 450.9900055

Advice to Management:
	•	Offer loyalty discounts or exclusive offers
	•	Bundle products or offer free shipping
	•	Personalized marketing emails
	•	Investigate if they’re receiving poor service/shipping delays
				
5.KMS Incurred the most shipping cost using which shiping methos?			

ship_mode	Total_shipping_cost			
Delivery Truck	51971.93974			
Regular Air	48008.18981			
Express Air	7850.909962			
				
6.Who are the most valuable customers, and what products or services do they typically purchase?			

Customer_name	         Total_sales			
Emily Phan	          117124.4353			
Deborah Brumfield	  97433.13462			
Roy Skaria	          92542.15319			
Sylvia Foulston	          88875.75812			
Grant Carroll	          88417.00061			
Alejandro Grove	          83561.93138			
Darren Budd	          81577.34305			
Julia Barnett	          80044.45286			
John Lucas	          79696.18585			
Liz MacKendrick	          76306.43164			
				
6b. what products or services do they typically purchase?				

customer_name	        product_category			
Muhammed MacIntyre	Office Supplies			
Ruben Dartt	        Office Supplies			
Liz Pelletier	        Furniture			
Liz Pelletier	        Furniture			
Liz Pelletier	        Technology			
Liz Pelletier	        Technology			
Julie Creighton	        Office Supplies			
Julie Creighton	         Technology			
Sample Company A	Technology			
Tamara Dahlen	        Technology			
				
7. Which small business customers had the highest sales?				

Customer_Name	Total_Sales			
Dennis Kane	75967.59322			
				
8.Which corporate customer placed the most number of order in 2009-2012				

Customer_Name	Total_Orders			
Adam Hart	27			
				
9. Which consumer customer was the most profitable one?				

Customer_Name	total_profit			
Emily Phan	34005.44			
				
10.Which customer returned items, and what segment do they belong to?				

customer_name	customer_segment			
    0	                0			
				
11. If the delivery truck is the most economical but the slowest shipping method and express air is the fastest but the most expensive one, do you think the company appropriately spent shipping costs based on the order priority? Explain your answer

Order_Priority	Ship_Mode	Total_Orders	Total_Shipping_Cost	
Critical	Delivery Truck	228	10783.81995	47.29745591
Critical	Express Air	200	1742.099988	8.71049994
Critical	Regular Air	1180	8586.759962	7.276915222
High	        Delivery Truck	248	11206.87994	45.189032
High	        Express Air	212	1453.529991	6.856273543
High	        Regular Air	1308	10005.00996	7.649090183
Low	        Delivery Truck	250	11131.60993	44.52643974
Low	         Express Air	190	1551.629998	8.166473673
Low	         Regular Air	1280	10263.61996	8.018453091
Medium	        Delivery Truck	205	9461.619975	46.15424378
Medium	        Express Air	201	1633.589993	8.127313397
Medium	         Regular Air	1225	9418.719966	7.688750992
Not Specified	 Delivery Truck	215	9388.009943	43.66516253
Not Specified	Express Air	180	1470.059992	8.166999957
Not Specified	Regular Air	1277	9734.079964	7.622615477
![image](https://github.com/user-attachments/assets/43c7ba56-4953-4bb4-a717-c9712a0383aa)


Based on the analysis, KMS mostly used Delivery Truck for low-priority orders and Express Air for high-priority ones, which indicates that shipping costs were appropriately allocated.
However, we found some Express Air shipments for Medium or Low priority orders, which may be optimized to reduce unnecessary cost.
We recommend enforcing shipping guidelines that link shipping method strictly to order priority for better cost control.

````SQL
select * from KMS
``````

```````SQL
-----------1. Which Product Category Had The Highest Sales? -
SELECT top 1 Product_Category, SUM(Sales) AS Total_Sales
FROM KMS
GROUP BY Product_Category
ORDER BY Total_Sales DESC
`````````

``````SQL
--------2a. What Are The Top 3  Region In Term Of Sales 
select top 3 REGION, SUM(Sales) AS Total_Sales
from KMS
GROUP BY REGION
order by TOTAL_SALES DESC
```````

``````SQL
---------2b.What Are The Bottom 3  Region In Term Of Sales
select top 3 REGION, SUM(Sales) AS Total_Sales
from KMS
GROUP BY REGION
order by TOTAL_SALES asc
````````

`````````SQL
----------3. What were the total sales of appliance in Ontario?
select 'ontario' region, sum(sales) as appliance_sales
from KMS
WHERE PRODUCT_SUB_CATEGORY = 'APPLIANCES' 
AND Region = 'ONTARIO';
`````````

```````SQL
----------4. Advise the management of kms on what to do to increase the revenue from the bottom 10 customers
select top 10 Customer_name, SUM(sales) AS Total_sales
from KMS
GROUP BY Customer_name
order by TOTAL_sales asc
````````

````````SQL
---------5. KMS Incurred the most shipping cost using which shiping methos?
select ship_mode, SUM(shipping_cost) AS Total_shipping_cost
from KMS
GROUP BY ship_mode
order by Total_shipping_cost desc
````````

``````````SQL
----------6. Who are the most valuable customers, and what products or services do they typically purchase?
select top 10 Customer_name, SUM(sales) AS Total_sales
from KMS
GROUP  BY Customer_name
order by TOTAL_sales desc
``````````

````````SQL
-------6b. what products or services do they typically purchase?

select top 10 * from (
      select customer_name, product_category
	        from KMS) as PURCHASE_COUNT 
````````````

``````SQL
select * from KMS
``````````

````````SQL
----------7. Which small business customers had the highest sales?
SELECT Customer_Name, SUM(Sales) AS Total_Sales
FROM kms
WHERE customer_Segment = 'Small Business'
GROUP BY Customer_Name
ORDER BY Total_Sales DESC
OFFSET 0 ROWS FETCH NEXT 1 ROWS ONLY;
````````

````````SQL
----------8.Which corporate customer placed the most number of order in 2009-2012
SELECT top 1 Customer_Name, COUNT(Order_ID) AS Total_Orders
FROM kms
WHERE customer_Segment = 'Corporate'
AND Order_Date BETWEEN '2009-01-01' AND '2012-12-31'
GROUP BY Customer_Name
ORDER BY Total_Orders DESC;
````````

``````SQL
-----------9. Which consumer customer was the most profitable one?
select top 1 Customer_Name, sum(profit) as total_profit
from kms
where customer_segment = 'consumer'
group by customer_name
order by total_profit desc;
```````

```````SQL
-----------10. Which customer returned items, and what segment do they belong to?
select distinct 0.customer_name, 0.customer_segment
from kms k
join  kms on k.Order_id = k.order_id;
````````

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
```````

# DSA-DATA-ANALYSIS-CAPSTONE-PROJECT-SQL-
This is my first project as a data analyst under DSA. I am not perfect, but I am learning and aiming to improve as I embark on this new journey.


``````SQL
SELECT top 1 Product_Category, SUM(Sales) AS Total_Sales
FROM KMS
GROUP BY Product_Category
ORDER BY Total_Sales DESC
```````

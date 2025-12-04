***Query 1-Top Products by Revenue***



SELECT Product,

&nbsp;      ROUND(SUM(Net\_Sales), 2) AS total\_revenue,

&nbsp;      ROUND(SUM(Profit), 2) AS total\_profit,

&nbsp;      SUM(Units) AS units\_sold

FROM Retail\_Sales

GROUP BY Product

ORDER BY total\_revenue DESC;



**Explanation**



This query identifies the highest revenue-generating products by aggregating Net\_Sales across all transactions.

It also includes total profit and total units sold to show whether high revenue is driven by margins, volume, or both.



**Insight from query 1**



Ball is the best-selling product.



File Folder and Pen also generate strong revenue.



Notebook and some others run at a negative profit — actionable insight.





***Query 2 Monthly total sales***



SELECT substr (Month\_Start,7,4) || '-' || substr (Month\_Start,4,2) as year\_month,

round (sum (Net\_Sales),2) as monthly\_sales,

sum (Profit) as monthly\_profit

from Retail\_Sales

group by year\_month

order by year\_month;



**Explanation**



This query converts the Month\_Start field into YYYY-MM format and aggregates both revenue (Net\_Sales) and profit for each month.

It helps identify monthly trends, seasonality, and whether sales peaks align with profit peaks.



**Insight from query 2**



February is the only unprofitable month: despite ₹112K in sales, profit fell to –₹14K, indicating high discounts or low-margin products.



March is the best month overall, with the highest revenue (₹176K) and highest profit (₹40K).



Revenue levels dip in February and then recover sharply in March, showing a U-shaped trend across the quarter.



Profit margins vary heavily—February has a negative margin, while March shows the strongest margin performance.



***Query 3 Region wise performance***



SELECT

Region,

count(\*) as line\_items,

sum (Units) as unit\_sold,

Sum (Net\_Sales) as total\_revenue,

sum (Profit) as total\_profit,

ROUND(AVG(Profit\_Margin),4) AS avg\_profit\_margin

from Retail\_Sales

group by Region

order by total\_revenue DESC;



**Explanation**



Aggregates key KPIs by Region so you can see which regions drive the most line\_items , volume and revenue — and whether high revenue regions are profitable (avg\_profit\_margin).



**Insight from query 3**



North is the strongest region, leading in units sold (4566) and revenue (₹132K) with the highest total profit (~₹24.6K).



East shows moderate revenue (₹108K) but significantly lower profit (~₹8.5K), indicating a weaker product mix or higher costs.



South delivers good revenue (₹91K) but has the worst average profit margin, suggesting deeper discounts or unprofitable SKUs.



West is the smallest region, both in sales volume and revenue, but maintains a better margin than South/East despite lower scale.



***Query 4 Products with Consistent Negative Profit***



SELECT

&nbsp; Product,

&nbsp; SUM(Units)        AS total\_units,

&nbsp; ROUND(SUM(Net\_Sales),2) AS total\_revenue,

&nbsp; ROUND(SUM(Profit),2)    AS total\_profit,

&nbsp; ROUND(AVG(Profit\_Margin),4) AS avg\_profit\_margin

FROM Retail\_Sales

GROUP BY Product

HAVING SUM(Profit) < 0

ORDER BY total\_profit ASC

LIMIT 20;



**Explanation**



Identifies SKUs that lose money overall (total\_profit < 0). Use this to flag products for price/cost review, promotional cuts, or delisting.



**Insight from query 4**



Three products — Water Bottle, Glue Stick, and Notebook — generate positive revenue but negative overall profit.

These products have very low or negative profit margins, meaning they are either priced too low, have high cost-per-unit, or involve heavy discounting.

They are strong candidates for price correction or discount control.



***Query 5 — Top 10 Products by Units Sold***



SELECT 

&nbsp;   Product,

&nbsp;   SUM(Units) AS total\_units\_sold,

&nbsp;   ROUND(SUM(Net\_Sales), 2) AS total\_revenue,

&nbsp;   ROUND(SUM(Profit), 2) AS total\_profit

FROM Retail\_Sales

GROUP BY Product

ORDER BY total\_units\_sold DESC

LIMIT 10;



**Explanation**



This query ranks products based on units sold to identify the highest-demand items. It also shows their total revenue and profit to highlight whether high-volume products are contributing financially or just moving units without margin.



**Insight from query 5**



Ball leads in total units sold (3012 units), making it the highest-volume product.



File Folder and Pen also show strong unit sales, indicating consistent demand.



Glue Stick and Water Bottle appear in the high-volume list but generate negative total profit, meaning high volume doesn’t always equal profitability.



Notebook ranks lowest among the top 10 in both units sold and profit, indicating weak performance.



***Query 6 — Dataset Validation (Sales, Cost, Profit Consistency)***



SELECT

&nbsp;   ROUND(SUM(Net\_Sales), 2) AS total\_net\_sales,

&nbsp;   ROUND(SUM(Total\_Cost), 2) AS total\_cost,

&nbsp;   ROUND(SUM(Profit), 2) AS total\_profit,

&nbsp;   ROUND(SUM(Net\_Sales) - SUM(Total\_Cost), 2) AS expected\_profit,

&nbsp;   ROUND(SUM(Profit), 2) = ROUND(SUM(Net\_Sales) - SUM(Total\_Cost), 2) 

&nbsp;       AS profit\_matches\_expected

FROM Retail\_Sales;



**Explanation**



Validation check confirms dataset consistency — total Profit matches Net Sales minus Total Cost.



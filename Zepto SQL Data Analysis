create table zepto(
sku_id SERIAL PRIMARY KEY,
category varchar(50),
name varchar(50) not null,
mrp numeric(9,2),
availableQunatity INT,
discountPercent NUMERIC(9,2),
discountedSellingPrice NUMERIC(8,2),
weightInGms INT,
outOfStock BOOLEAN,
quantity INT
);

UPDATE zepto
SET 
    availableQunatity = discountPercent,
    discountPercent = availableQunatity;
select * from zepto;

--DATA EXPLORATION
--null values
select * from zepto
WHERE name is null
or
category is null
or
mrp is null
or
availablequnatity is null
or
discountPercent is null
or
weightInGms is null
or
outOfStock is null
or
quantity is null;

--differentproductcategories
SELECT distinct category
from zepto
order by category;

--product in stock vs out of stock
SELECT outOfStock, COUNT(sku_id)
from zepto
Group by outOfStock;

--data cleaning
Select* from zepto 
where mrp = 0 or discountedSellingPrice = 0;

Delete From zepto 
where mrp='0' ;

--convert paise into rupees
update zepto
set mrp= mrp/100.0,
discountedSellingPrice = discountedSellingPrice/100.0;

Select mrp, discountedSellingPrice from zepto;

Q1 -- TOP DISCOUNTED PRODUCTS
SELECT name, mrp, discountPercent
from zepto
order by discountPercent desc
LIMIT 5;

q2 -- HIGHEST PRICED PRODUCTS
Select name, mrp
from zepto
order by mrp desc 
limit 10;

q3 --OUT OF STOCK PRODUCTS
SELECT name,mrp, outOfStock
from zepto
where outOfStock='true';

q4 --Price range segmentation
SELECT mrp, name,
    CASE
        WHEN mrp < 200 THEN 'low'
        WHEN mrp BETWEEN 200 AND 800 THEN 'medium'
        ELSE 'high'
    END AS price_range
FROM zepto;

q5 --estimated revenue for each category
SELECT category,
    SUM(discountedSellingPrice * availableQunatity) AS total_revenue
FROM zepto
GROUP BY category
ORDER BY total_revenUe;

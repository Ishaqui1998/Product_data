
# Product Analysis
# Top 5 Product Ratings 
select `Product Name`, `product ratings`
from product_data
order by `Product Ratings` desc
limit 5;

# Products out-of-stock
select `Product Name`
from product_data
where `stock Quantity` = 0;


# top 5 products have the highest quantity sold
select `product name`, `stock quantity`
from product_data
order by `Stock Quantity` desc limit 5;

# Total inventory value for each product
select `product name`, price, `stock quantity`, (price * `stock quantity`) as inventory_value
from product_data;

# Products having stocks less than 10
select `product name`, `stock quantity`
from product_data
where `stock quantity` < 10;

SELECT COUNT(*) AS low_stock_count
FROM product_data
WHERE `stock quantity` < 10;

# Products available in each quantity
select `product category`, count(*) as product_count
from product_data
group by `product category`;

# Category having the highest stock quantity
select `product category`, sum(`stock quantity`) as Total_stock
from product_data
group by `product category`
order by Total_stock desc;

# Avg product price
select `product category`, round(avg(price),2) as avg_price
from product_data
Group by `product category`;

# Products that expired
select `product name`, `Expiration date`
from product_data
where `Expiration Date`< curdate();

# list products manufactured in 6 months
SELECT `Product Name`, `Manufacturing Date` 
FROM product_data
 WHERE `Manufacturing Date` >= DATE_SUB(CURDATE(), INTERVAL 6 MONTH);
 
# Products having less than 3 stars
select `product name`, `product ratings`, price
from product_data
where `product ratings` < 3;


SELECT `Product Name`, `Stock Quantity`, `Product Ratings` 
FROM product_data
WHERE `Stock Quantity` < 5 AND `Product Ratings` < 3;

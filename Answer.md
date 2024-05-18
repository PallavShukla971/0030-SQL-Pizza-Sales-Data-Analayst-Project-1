|||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||

Answers to Questions:
____________________________________________________________

Basic:

-- 1. Retrieve the total number of orders placed.
 -> SELECT 
    COUNT(order_id) AS total_orders
FROM
    orders;

-- 2. Calculate the total revenue generated from pizza sales.
 -> SELECT 
    ROUND(SUM(order_details.quantity * pizzas.price),
            2) AS total_sales
FROM
    order_details
        JOIN
    pizzas ON pizzas.pizza_id = order_details.pizza_id

-- 3. Identify the highest-priced pizza.
 -> SELECT 
    pizza_types.name, pizzas.price
FROM
    pizza_types
        JOIN
    pizzas ON pizza_types.pizza_type_id = pizzas.pizza_type_id
ORDER BY pizzas.price DESC
LIMIT 1;

-- 4. Identify the most common pizza size ordered.
 -> -- we first take out the count of quantity ordered
SELECT 
    quantity, COUNT(order_details_id)
FROM
    order_details
GROUP BY quantity;

-- now pizza size in pizzas and how many how many ordered in order details

SELECT 
    pizzas.size,
    COUNT(order_details.order_details_id) AS order_count
FROM
    pizzas
        JOIN
    order_details ON pizzas.pizza_id = order_details.pizza_id
GROUP BY pizzas.size
ORDER BY order_count DESC; 

-- 5. List the top 5 most ordered pizza types along with their quantities.
 -> SELECT 
    pizzas.size,
    COUNT(order_details.order_details_id) AS order_count
FROM
    pizzas
        JOIN
    order_details ON pizzas.pizza_id = order_details.pizza_id
GROUP BY pizzas.size
ORDER BY order_count DESC;

-- 5. List the top 5 most ordered pizza types 
-- along with their quantities.

SELECT 
    pizza_types.name, 
    SUM(order_details.quantity) AS quantity
FROM
    pizza_types
        JOIN
    pizzas ON pizza_types.pizza_type_id = pizzas.pizza_type_id
        JOIN
    order_details ON order_details.pizza_id = pizzas.pizza_id
GROUP BY pizza_types.name
ORDER BY quantity DESC
LIMIT 5;


____________________________________________________________

Intermediate:

-- 6. Join the necessary tables to find the total quantity of each pizza category ordered.
 -> 

-- 7. Determine the distribution of orders by hour of the day.
 -> 

-- 8. Join relevant tables to find the category-wise distribution of pizzas.
 -> 

-- 9. Group the orders by date and calculate the average number of pizzas ordered per day.
 -> 

-- 10. Determine the top 3 most ordered pizza types based on revenue.
 -> 
____________________________________________________________


Advanced:

-- 11. Calculate the percentage contribution of each pizza type to total revenue.
 -> 

-- 12. Analyze the cumulative revenue generated over time.
 -> 

-- 13. Determine the top 3 most ordered pizza types based on revenue for each pizza category.
 -> 

____________________________________________________________


|||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||

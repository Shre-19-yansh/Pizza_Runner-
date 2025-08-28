# A. Pizza Metrics
Q1. How many pizzas were ordered?
``` SQL
SELECT COUNT(pizza_id) AS Total_Pizza_Ordered
FROM customer_orders;
```
<img width="241" height="69" alt="image" src="https://github.com/user-attachments/assets/487ca42e-b68f-4a62-8f1a-068da5dd1717" />

- Total Pizza Ordered were 14
  
Q2. How many unique customer orders were made?
``` SQL
SELECT COUNT(DISTINCT customer_id) AS Customers_Order
FROM customer_orders;

```
<img width="204" height="60" alt="image" src="https://github.com/user-attachments/assets/1349e75d-d02f-40a1-be6b-6635b9ffef06" />

 - There are total 5 unique customer orders
   
Q3. How many successful orders were delivered by runner?
``` SQL
SELECT COUNT(duration) AS pizza_delivered
FROM runner_orders
WHERE duration IS NOT NULL;
```
<img width="277" height="90" alt="image" src="https://github.com/user-attachments/assets/f0190bd2-f922-402d-a522-48cc9aba72a0" />

- 8 deliveries were successfull 

Q4. How many of each type of pizza was delivered?
``` SQL
SELECT pizza_id, COUNT(pizza_id) AS Total
FROM customer_orders
GROUP BY pizza_id;
```
<img width="192" height="84" alt="image" src="https://github.com/user-attachments/assets/7d5cf03b-c4b2-44a6-9809-d2060f3bf2ad" />

- 10 pizza of Meat Lover were delivered
- 4 pizza of Vegetarian were delivered
  
Q5.How many Vegetarian and Meatlovers were ordered by each customer?
``` SQL
SELECT 
    customer_orders.customer_id, 
    pizza_names.pizza_name,
    COUNT(customer_orders.pizza_id)
FROM customer_orders
JOIN pizza_names
ON customer_orders.pizza_id=pizza_names.pizza_id
GROUP BY customer_orders.customer_id, pizza_names.pizza_name
ORDER BY customer_orders.customer_id;

```
<img width="554" height="241" alt="image" src="https://github.com/user-attachments/assets/6cb98672-089a-4b11-84a8-b82dbd203511" />

- Customer_id 101 ordered 2 Meat Lover and 1 Vegetarian
- Customer_id 102 ordered 2 Meat Lover and 1 Vegetarian
- Customer_id 103 ordered 3 Meat Lover and 1 Vegetarian
- Customer_id 104 ordered 3 Meat Lover
- Customer_id 105 ordered 1 Vegetarian
  
Q6. What was the maximum number of pizzas delivered in a single order?
``` SQL
SELECT order_id, COUNT(pizza_id) AS pizza_count
FROM customer_orders
GROUP BY order_id
ORDER BY pizza_count DESC
LIMIT 1;

```
<img width="245" height="59" alt="image" src="https://github.com/user-attachments/assets/400b9b9d-fac8-41ed-b6c7-1be34996e089" />

- 3 is the maximum pizza delivered in order_id 4  

Q7. For each customer, how many delivered pizzas had at least 1 change and how many had no changes?
``` SQL
SELECT customer_orders.customer_id, 
   COUNT(
          CASE
              WHEN (customer_orders.extras > 0 OR customer_orders.exclusions > 0)
                   AND runner_orders.duration IS NOT NULL
              THEN 1 
          END
        ) AS Pizza_with_Change,
   COUNT(
          CASE 
              WHEN (customer_orders.extras < 1 AND customer_orders.exclusions < 1)
                   AND runner_orders.duration IS NOT NULL
              THEN 1
          END
        ) AS Pizza_with_no_change
FROM customer_orders
JOIN runner_orders
    ON customer_orders.order_id = runner_orders.order_id
GROUP BY customer_orders.customer_id;

```
<img width="520" height="167" alt="image" src="https://github.com/user-attachments/assets/50945df4-d702-4daf-b2a9-26465bcd921f" />

- Customer_101 ordered 0 pizza with change and 2 with no change
- Customer_102 ordered 0 pizza with change and 3 with no changes
- Customer_103 orderd 3 pizza with changes and 0 with no changes
- Customer_104 ordered 2 pizza with changes and 1 with no changes
- Customer_105 ordered 1 pizza with changes an d0 with no change
- Total pizza delivered with changes are 6 and without chages are also 6

Q8. How many pizzas were delivered that had both exclusions and extras?
``` SQL
SELECT 
    SUM(
        CASE 
            WHEN customer_orders.exclusions IS NOT NULL 
                 AND customer_orders.extras IS NOT NULL 
                 AND customer_orders.exclusions <> '' 
                 AND customer_orders.extras <> '' 
            THEN 1 
            ELSE 0 
        END
    ) AS pizza_count_w_exclusions_extras
FROM customer_orders
JOIN runner_orders
    ON customer_orders.order_id = runner_orders.order_id
WHERE runner_orders.distance >= 1;

```
<img width="323" height="57" alt="image" src="https://github.com/user-attachments/assets/0706f411-6f07-40d9-b59a-028a5fdd7f66" />

- only 1 pizza was delivered which had both exlcusions and extras
  
Q9. What was the total volume of pizzas ordered for each hour of the day?
``` SQL
SELECT hour_day, COUNT(pizza_id) AS Total_pizza_ordered
FROM customer_orders
GROUP BY hour_day;
```
<img width="314" height="191" alt="image" src="https://github.com/user-attachments/assets/2586587c-244e-4abe-9d97-54f3da7c213d" />

- Hour 11 = 1 pizza
- Hour 13 = 3 pizza
- Hour 18 = 3 pizza
- Hour 19 = 1 pizza
- Hour 21 - 3 pizza
- hour 23 = 3 pizza
  
Q10. What was the volume of orders for each day of the week?
``` SQL
SELECT Day_week, COUNT(pizza_id) AS total_pizza_ordered
FROM customer_orders
GROUP BY Day_week;

```
<img width="319" height="142" alt="image" src="https://github.com/user-attachments/assets/b41d45f9-6408-4a8b-8bbf-f470abe81664" />

- 5 pizza was delivered on Friday
- 3 pizza was deliveed on Saturday
- 5 pizza was delivered on Monday
- 1 pizza was delivered on Sunday
  
# B. Runner and Customer Experience
Q1. How many runners signed up for each 1 week period? (i.e. week starts 2021-01-01)
``` SQL
SELECT week_no, COUNT(registration_date)
FROM runners
GROUP BY week_no
ORDER BY week_no;

```
<img width="354" height="107" alt="image" src="https://github.com/user-attachments/assets/2d299454-070f-44c4-9911-3a3dca202c4c" />

- 2 runner registered in week 1
- 1 runner registered in week 2
- 1 runner registered in week 3
  
Q2. What was the average time in minutes it took for each runner to arrive at the Pizza Runner HQ to pickup the order?
``` SQL
```
Q3. Is there any relationship between the number of pizzas and how long the order takes to prepare?
``` SQL
```
Q4. What was the average distance travelled for each customer?
``` SQL
SELECT customer_orders.customer_id, AVG(runner_orders.distance) AS Avr_Distance
FROM customer_orders
JOIN runner_orders
ON customer_orders.order_id=runner_orders.order_id
GROUP BY customer_orders.customer_id
ORDER BY customer_orders.customer_id;
```
<img width="348" height="160" alt="image" src="https://github.com/user-attachments/assets/fbee8089-efad-4a36-b657-6131aee4e8db" />

- 20km travelled for customer_id 101
- 16.73km travelled for customer_id 102
- 23.39km travlled for customer_id 103
- 10km travelled for customer_id 104
- 25km travelled for customer_id 105
  
Q5. What was the difference between the longest and shortest delivery times for all orders?
``` SQL
SELECT order_id, runner_id, (distance / (duration / 60)) AS average_speed
FROM runner_orders
ORDER BY order_id;
```
<img width="144" height="59" alt="image" src="https://github.com/user-attachments/assets/d701a1ee-9883-4130-9b4a-2b1372d037c6" />

- The difference is of 30 minutes
  
Q6. What was the total average speed for runner for delivery and do you notice any trend for these values?
``` SQL
SELECT order_id, runner_id, (distance / (duration / 60)) AS average_speed
FROM runner_orders
ORDER BY order_id;
```
<img width="410" height="298" alt="image" src="https://github.com/user-attachments/assets/3d931a27-2723-48df-80bb-d29921b9eaf7" />

- Average speed for order__id 1 is 37.50
- Average speed for order_id 2 is 44.44
- Average speed for order_id 3 is 40.20
- Average speed for order_id 4 is 35.10
- Average speed for order_id 5 is 40
- Average speed for order_id 7 is 60.00
- Average speed for order_id 8 is 93.6
- Avergae speed for order_id 10 is 60.00
  
Q7. What is the successful delivery percentage of the runner?
``` SQL
SELECT 
    100* SUM(CASE WHEN cancellation = 'NA' THEN 1 ELSE 0 END) / COUNT(*) 
    AS Delivery_Percentage
FROM runner_orders;
```
<img width="223" height="72" alt="image" src="https://github.com/user-attachments/assets/97a1acca-0555-4e3a-8371-6d6624dc2a2a" />

- the Dlivery percentage is 80.00 %
  
# C. Ingredient Optimisation
Q1. What are the standard ingredients for each pizza?
``` SQL
SELECT *
FROM pizza_recipes;
```
<img width="310" height="88" alt="image" src="https://github.com/user-attachments/assets/51402529-02a7-4f17-a179-18b70f42466d" />

- Pizza_id 1 has toppings 1, 2, 3, 4, 5, 6, 8, 10
- Pizza_id 2 had toppings 4, 6, 7, 9, 11, 12
  
Q2. What was the most commonly added extra?
``` SQL
SELECT '1' AS extra, COUNT(*) AS extra_count
FROM customer_orders
WHERE FIND_IN_SET('1', REPLACE(extras, ' ', '')) > 0
UNION ALL
SELECT '4', COUNT(*)
FROM customer_orders
WHERE FIND_IN_SET('4', REPLACE(extras, ' ', '')) > 0
UNION ALL
SELECT '5', COUNT(*)
FROM customer_orders
WHERE FIND_IN_SET('5', REPLACE(extras, ' ', '')) > 0;
```
<img width="226" height="120" alt="image" src="https://github.com/user-attachments/assets/4346280e-5495-48c5-94fa-a1b8fcc72c6a" />

- Extra 1 is used 4 times
- Extra 4 is used 1 time
- Extra 5 is used 1 time
  
Q3.What was the most common exclusion?
``` SQL
SELECT '4', COUNT(*)
FROM customer_orders
WHERE FIND_IN_SET('4', exclusions) > 0
UNION ALL
SELECT '2', COUNT(*)
FROM customer_orders
WHERE FIND_IN_SET('2', exclusions) > 0
UNION ALL
SELECT '6', COUNT(*)
FROM customer_orders
WHERE FIND_IN_SET('6', exclusions) > 0;
```
<img width="203" height="117" alt="image" src="https://github.com/user-attachments/assets/c71ce4d8-a373-4976-9571-4fc00809764e" />

- Topping 4 is excluded 4 times
- Topping 2 is excluded 2 times
- Topping 6 is excluded 0 times
  
Q4. Generate an order item for each record in the customers_orders table in the format of one of the following:
 Meat Lovers
    ```SQL
    SELECT *
    FROM customer_orders
    WHERE pizza_id=1
    ```
 <img width="731" height="306" alt="image" src="https://github.com/user-attachments/assets/f0cef8c1-62e1-4295-94c2-bac87ddef619" />

- Customer_id 101, 102, 103, 104 have ordered Meat Lover pizza
- Total 10 Meat Lover pizza were ordered
  
Meat Lovers - Exclude Beef
``` SQL
SELECT *
FROM customer_orders
WHERE exclusions = '3'
```
<img width="735" height="100" alt="image" src="https://github.com/user-attachments/assets/f6289305-9693-4133-b258-45ae2d898b6d" />

- 0 orders
  
Meat Lovers - Extra Bacon
 ```SQL
SELECT *
FROM customer_orders
WHERE FIND_IN_SET('1', extras)>0
<img width="731" height="150" alt="image" src="https://github.com/user-attachments/assets/67613200-d9f7-498c-a7b3-d003a4053bdb" />
```
<img width="731" height="150" alt="image" src="https://github.com/user-attachments/assets/c5efaf2b-beb1-438a-a69a-59bbbd0a1746" />

- Customer_id 103, 104, 105 have ordered meat lover with extra bacon
- Total 4 orders were made.
  
Meat Lovers - Exclude Cheese, Bacon - Extra Mushroom, Peppers
```SQL
SELECT *
FROM customer_orders
WHERE exclusions = '1' AND '4'
UNION
SELECT *
FROM customer_orders
WHERE extras = '6' AND '9'
```
<img width="734" height="98" alt="image" src="https://github.com/user-attachments/assets/be31895b-cf54-4e2b-9ef3-b9c1cc4cfa8b" />

- 0 orders

Q5. Generate an alphabetically ordered comma separated ingredient list for each pizza order from the customer_orders table and add a 2x in front of any relevant ingredients
For example: "Meat Lovers: 2xBacon, Beef, ... , Salami"
``` SQL
SELECT customer_orders.order_id, pizza_recipes.toppings
FROM customer_orders
JOIN pizza_recipes 
  ON customer_orders.pizza_id = pizza_recipes.pizza_id
ORDER BY customer_orders.order_id;
```
<img width="317" height="413" alt="image" src="https://github.com/user-attachments/assets/348a7661-2405-49f1-8105-30d049ab5ccb" />

- Order_id 1 = 1,2,3,4,5,6,8,10
- order_id 2 = 1,2,3,4,5,6,8,10
- Order_id 3 = 1,2,3,4,5,6,8,10 and 4,6,7,9,11,12
- Order_id 4 = 1,2,3,4,5,6,8,10 and 1,2,3,4,5,6,8,10 and 4,6,7,9,11,12
- Order_id 5 = 1,2,3,4,5,6,8,10
- Order_id 6 = 4,6,7,9,11,12
- Order_id 7 = 4,6,7,9,11,12
- Order_id 8 = 1,23,4,5,6,8,10
- Order_id 9 = 1,2,3,4,5,6,8,10
- Order_id 10 = 1,2,3,4,5,6,8,10 and 1,2,3,4,5,6,8,10
  
Q6. What is the total quantity of each ingredient used in all delivered pizzas sorted by most frequent first?
``` SQL
```

# 🍕 Pizza Runner – SQL Challenge 2  
<img width="835" height="834" alt="Screenshot 2025-08-27 191417" src="https://github.com/user-attachments/assets/bc5a4987-1260-4f1e-83f1-e9126fbb32c5" />

## 📖 Project Overview  
This project is part of the **8 Week SQL Challenge**, focusing on the **Pizza Runner case study**.  
The challenge simulates a real-world food delivery startup where messy datasets need to be cleaned and analyzed.  

The main aim is to prepare the data for insights into:  
- 🍕 Pizza orders and customer preferences  
- 🏃 Runner performance and delivery efficiency  
- 📈 Business growth and operational improvements  

---

## 🎯 Objective  
- 🧹 Clean and standardize multiple tables with messy, inconsistent data  
- 🔗 Normalize multi-value fields (toppings, extras, exclusions)  
- 📊 Combine datasets through joins for analysis  
- 💡 Generate insights about customers, pizzas, and delivery operations  

---

## 📂 Files in This Repository  
- `customer_orders.csv` → Customer pizza orders
- `pizza_names.csv` → Pizza ID and name mapping
- `pizza_recipes.csv` → Standard recipes for each pizza
- `pizza_toppings.csv` → Mapping of topping ID to topping names
- `runner_orders.csv` → Runner assignments, times, and cancellations  
- `runners.csv` → Runner registration details  
- `Case_Study_Solution.md` → SQL queries used for cleaning and analysis  
- `README.md` → Project documentation  

---

## 🧹 Data Cleaning  
During the cleaning process, the following tasks were performed:  

1. **Splitting DateTime Columns** – Separated order and pickup timestamps into `order_date`, `order_time`, `pickup_date`, and `pickup_time` for easier analysis.  
2. **Standardizing Units** – Removed text suffixes like `km`, `minutes`, `min` to make distance and duration values consistent numeric formats.  
3. **Handling Nulls** – Replaced `null`, `NaN`, and blanks with `NO` in categorical columns.  
4. **Cleaning Exclusions & Extras** – Replaced `NULL` values with blanks to ensure consistency.  

---

## 📊 Expected Outcomes  
- ✅ A cleaned and reliable dataset for analysis  
- 📈 Insights into customer order patterns (popular pizzas, toppings, exclusions/extras)  
- 🚚 Runner performance metrics (average speed, distance, cancellations)  
- 💡 Foundation for further business recommendations  

---
## 🔄 Process  

1. Understand the schema
- Reviewed the Entity Relationship Diagram (ERD) and table structures to comprehend how customer_orders, runner_orders, runners, pizza_names, 
  pizza_recipes, and pizza_toppings are related. This helped identify the joins required for analysis.
  <img width="359" height="161" alt="image" src="https://github.com/user-attachments/assets/b3dd9d21-0f7b-4d70-afbb-4bc44f5d037c" />
2. Identify data issues
- Examined each table for missing values, inconsistent text formats, multi-value fields (like toppings, exclusions, extras), and anomalies in date,
  time, distance, and duration columns that could affect analysis.
3. Cleaning data
 - Performed cleaning in Excel before uploading to MySQL. This included splitting combined date-time fields into separate date and time columns, standardizing distance and
   duration by removing text like km and minutes, and replacing blanks, nulls, and NaN values with consistent placeholders.
4. Normalize recipes/toppings
 - Broke down multi-value fields into atomic values for easier aggregation. Ensured toppings, extras, and exclusions were consistently
   represented across orders to allow accurate calculation of ingredient usage and pizza metrics.
5. Answer case study questions
- Wrote SQL queries to generate insights on pizza metrics, runner performance, customer patterns, and ingredient optimization. Verified outputs
  against expected business scenarios to ensure accuracy.
6. Document findings
- Summarized the cleaned data and query results in a structured format. This documentation can guide business decisions and provide a foundation for
  future analysis without needing to re-run all queries.
---

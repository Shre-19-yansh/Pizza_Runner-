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
1. **Understand the schema** – Reviewed ERD and table relationships
   <img width="766" height="337" alt="Screenshot 2025-08-27 191557" src="https://github.com/user-attachments/assets/cf118377-0171-4f0f-bc82-8d5ac9fca5f4" />
3. **Identify data issues** – Missing values, inconsistent text, multi-value fields  
4. **Cleaning data** – Applied string functions, casting, and formatting  
5. **Normalize recipes/toppings** – Broke down multi-value fields into atomic values  
6. **Answer case study questions** – Wrote SQL queries to derive insights  
7. **Document findings** – Summarized results in structured format  

---

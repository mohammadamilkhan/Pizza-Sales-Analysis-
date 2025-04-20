# Pizza Sales Analysis

![image](https://github.com/user-attachments/assets/974f2948-1fb4-4efe-b760-49449586d901)

# Problem Statement & Project Objective

## Problem Statement

The pizza business lacks visibility into key sales metrics, customer behavior, and product performance. Without data-driven insights, it's difficult to make informed decisions for menu planning, marketing, and operational efficiency.

## Project Objective

- Analyze sales data using SQL and Power BI.
- Identify trends in customer purchasing patterns.
- Determine top-performing and underperforming pizzas.
- Enable data-driven decisions to optimize the menu and maximize revenue.

---

# Project Process Overview

## 1: Data Collection

Dataset of pizza orders including order date, time, category, size, quantity, and price.

## 2: Data Cleaning & Preparation

Handled nulls, standardized formats, and ensured consistency using Power Query.

## 3: Exploratory Data Analysis (SQL)

Derived KPIs and insights: total revenue, order trends, best/worst sellers, etc.

## 4: Dashboard Design (Power BI)

Built interactive visuals and KPIs for clear business insights.

## 5: Insight Generation & Recommendation

Interpreted visual and SQL insights for strategic decision-making.

# Pizza Sales Analysis - KPIs & Visual Insights

## KPIs and Their Insights

| KPI                  | Value    | Insight                                                                 |
| -------------------- | -------- | ----------------------------------------------------------------------- |
| Total Revenue        | $817,860 | Strong sales performance across the dataset period.                     |
| Average Order Value  | $38.31   | Each order on average contributes significantly to revenue.             |
| Total Pizzas Sold    | 49,574   | High volume of individual pizza sales.                                  |
| Total Orders         | 21,350   | Steady stream of customer orders.                                       |
| Average Pizzas/Order | 2        | On average, customers purchase 2 pizzas per order—group ordering trend. |

---

## Charts & Visual Insights

### 1. % of Sales by Pizza Category

- **Categories**: Classic, Supreme, Chicken, Veggie
- **Insight**: Classic pizzas dominate sales revenue followed by Supreme. Chicken and Veggie trail behind.

### 2. % of Sales by Size

- **Sizes**: L, M, S, XL, XXL
- **Insight**: Large (L) and Medium (M) pizzas contribute the highest revenue. Small and extra-large sizes have lower contribution; XXL is negligible.

### 3. Quantities Sold by Size

- **L size**: 18,956 units (Most popular)
- **M size**: 15,635 units
- **Insight**: Customers prefer larger portions; XXL is least preferred (28 units only).

### 4. Day-wise Trend of Orders

- **Friday** has the highest orders (3.54k), followed by **Thursday** and **Saturday**
- **Insight**: Peak sales towards the weekend—possibly due to social/family gatherings.

### 5. Hour-wise Trend of Orders

- **Peak hours**: 12 PM - 2 PM and 6 PM - 8 PM
- **Insight**: Lunch and dinner time drive majority of the orders.

### 6. Top 3 Best Selling Pizzas

- The Classic Deluxe Pizza
- The Barbecue Chicken Pizza
- The Hawaiian Pizza
- **Insight**: These items should be featured and promoted more.

### 7. Bottom 3 Least Sold Pizzas

- The Calabrese Pizza
- The Mediterranean Pizza
- The Brie Carre Pizza
- **Insight**: Consider reviewing pricing, visibility, or removing from menu.

# Pizza Sales Analysis - SQL Queries & Insights

## 1. Total Revenue

```sql
SELECT ROUND(SUM(total_price),2) AS total_revenue FROM pizza_sales;
```

**Insight**: Total revenue generated is `$817,860`.

---

## 2. Average Order Value

```sql
SELECT ROUND((SUM(total_price) / COUNT(DISTINCT order_id)),2) AS avg_order_value FROM pizza_sales;
```

**Insight**: Customers spend about `$38.31` per order.

---

## 3. Total Pizzas Sold

```sql
SELECT SUM(quantity) AS total_pizzas_sold FROM pizza_sales;
```

**Insight**: 49,574 pizzas sold in total.

---

## 4. Total Orders

```sql
SELECT COUNT(DISTINCT order_id) AS total_orders FROM pizza_sales;
```

**Insight**: 21,350 orders placed.

---

## 5. Average Pizzas per Order

```sql
SELECT ROUND((SUM(quantity) / COUNT(DISTINCT order_id)),2) AS avg_pizzas_per_order FROM pizza_sales;
```

**Insight**: On average, each order has 2 pizzas.

---

## 6. Day-wise Trend of Orders

```sql
SELECT DAYNAME(order_date) AS order_day, COUNT(DISTINCT order_id) AS daily_trend_of_orders
FROM pizza_sales
GROUP BY order_day;
```

**Insight**: Peak days = **Friday > Thursday > Saturday**.

---

## 7. Hourly Trend of Orders

```sql
SELECT HOUR(order_time) AS order_hours, COUNT(DISTINCT order_id) AS hourly_trend_of_orders
FROM pizza_sales
GROUP BY order_hours
ORDER BY order_hours;
```

**Insight**: Peak hours = **12 PM and 6 PM**.

---

## 8. Percentage of Sales by Pizza Category

```sql
SELECT pizza_category, ROUND(SUM(total_price),2) FROM pizza_sales GROUP BY pizza_category;
```

**Insight**: **Classic** leads in revenue followed by **Supreme**.

---

## 9. Percentage of Sales by Pizza Size

```sql
SELECT pizza_size, ROUND(SUM(total_price),2) FROM pizza_sales GROUP BY pizza_size;
```

**Insight**: L and M sizes drive most sales revenue.

---

## 10. Top 5 Pizzas by Revenue

```sql
SELECT pizza_name, SUM(total_price) AS total_revenue
FROM pizza_sales
GROUP BY pizza_name
ORDER BY total_revenue DESC
LIMIT 5;
```

**Insight**: Top performers in revenue generation.

---

## 11. Bottom 5 Pizzas by Revenue

```sql
SELECT pizza_name, SUM(total_price) AS total_revenue
FROM pizza_sales
GROUP BY pizza_name
ORDER BY total_revenue ASC
LIMIT 5;
```

**Insight**: Candidates for removal or improvement.

# Conclusion of Project

This **Pizza Sales Analysis** project offers a complete overview of business performance through **KPIs**, **visual trends**, and **SQL-driven insights**. The findings highlight that:

- **Customer behavior peaks** during weekends and meal times.
- **Large and Classic pizzas** are customer favorites.
- **Promotional efforts** should focus on best sellers and peak hours.
- **Underperforming pizzas** need re-evaluation.

The dashboard enables **effective data-driven decision-making** for menu optimization and marketing strategy.

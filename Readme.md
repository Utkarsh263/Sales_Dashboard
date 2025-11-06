# 🧠 Company Sales Analysis Dashboard (Power BI)

## 📊 Project Overview

This Power BI project showcases an end-to-end **Sales Analytics Dashboard** that helps visualize and analyze a company’s sales performance across time, products, customers, and regions.

The dashboard enables users to answer key business questions related to **sales growth**, **profitability**, **discount patterns**, **product performance**, and **geographical insights**, using data cleaning, transformation, and advanced **DAX-based calculations** in Power BI.

---

## 🎯 Project Objectives

The dashboard addresses the following analytical goals:

1. **Top/Bottom 5 Products** by Sales, Profit, and Quantity Sold.
2. **Sales Trends Over Time** (daily, monthly, quarterly, annually).
3. **Relationship Between Sales & Profit** through scatter plots.
4. **Comparison of Sales, Profit, and Quantity Sold** between two user-selected time periods.
5. **Average Discount Offered** under each promotion category.
6. **Total Number of Orders** processed.
7. **Detailed Order-Level Data** with interactive filters (Product, Date, Customer, Promotion).
8. **Sales by City** visualized on a geographic map.

---

## 🧹 Data Preparation and Cleaning

Performed using **Power Query Editor**:

* Removed nulls, duplicates, and inconsistent values.
* Standardized **date formats**, **text casing**, and **numeric data types**.
* Merged multiple tables — *Fact Table*, *Product Table*, *Customer Table*, and *Promotion Table* — using **joins**.
* Added **derived columns** and **custom transformations**, including:

  * `Total Sales = Units Sold * Price Per Unit`
  * `Discount Value = (Discount Percentage / 100) * Total Sales`
  * `Net Sale = Total Sales - Discount Value`
  * `Profit Margin = Profit / Net Sale`

Created **Date Hierarchies** (Year, Quarter, Month, Day) for time-based trends.

---

## 🧮 DAX Calculations

Below are the key **DAX measures** implemented in this project.

### 🔸 Comparative Period Measures

```DAX
Quantity Sold =
CALCULATE(
    SUM('Fact Table'[Units Sold]),
    ALL('Date Table 1'),
    USERELATIONSHIP('Date Table 2'[Date], 'Fact Table'[Date (dd/mm/yyyy)])
)
```

```DAX
Sum of Net Sales =
CALCULATE(
    SUM('Fact Table'[Net Sale]),
    ALL('Date Table 1'),
    USERELATIONSHIP('Date Table 2'[Date], 'Fact Table'[Date (dd/mm/yyyy)])
)
```

```DAX
Total Profit =
CALCULATE(
    SUM('Fact Table'[Profit]),
    ALL('Date Table 1'),
    USERELATIONSHIP('Date Table 2'[Date], 'Fact Table'[Date (dd/mm/yyyy)])
)
```

These measures activate the secondary date relationship (`Date Table 2`) to dynamically compare **two different time periods** selected by the user.

### 🔸 Base Aggregation Measure

```DAX
Sum Dim = SUM('Fact Table'[Net Sale])
```

### 🔸 Additional Key Measures

```DAX
Total Sales = SUM('Fact Table'[Total Sales])
Average Discount = AVERAGE('Fact Table'[Discount Percentage])
Total Orders = COUNTROWS('Fact Table')
Profit Margin % = DIVIDE([Total Profit], [Sum of Net Sales], 0)
```

---

## 📅 Dual Date Comparison Logic

The model uses **two independent Date Tables**:

* **Date Table 1:** Primary timeline for current period visuals.
* **Date Table 2:** Secondary timeline for comparative analysis (e.g., previous year or custom range).

By applying `USERELATIONSHIP()` in DAX, both time periods can be analyzed simultaneously for:

* Total Sales
* Total Profit
* Total Quantity Sold

---

## 📊 Dashboard Visuals and Insights

### 🖼️ **Question Slide**

![Question Slide](https://github.com/Utkarsh263/Sales_Dashboard/blob/main/Screenshot%202025-11-07%20004355.png)
This slide contains the project questions and problem statement — outlining analytical objectives like top/bottom product analysis, sales trends, discounts, and profit insights.

---

### 🖼️ **1️⃣ First Slide — Detailed Data Table View **

![Top & Bottom Products](https://github.com/Utkarsh263/Sales_Dashboard/blob/main/Screenshot%202025-11-07%20004217.png)

* Interactive table displaying Customer, Product, Promotion, Date, Price, Discount, Net Sale, and Profit.
* Includes slicers for **Date, Customer Name, Product Name, and Promotion Name**.

---

### 🖼️ **2️⃣ Second Slide — Detailed Data Table View**

![Detailed Data Table View](https://github.com/Utkarsh263/Sales_Dashboard/blob/main/Screenshot%202025-11-07%20004238.png)

* **Top 5 / Bottom 5 Products** by Sales, Quantity, and Profit.
* Highlights best-selling and underperforming items.

---

### 🖼️ **3️⃣ Third Slide — Comparative Period Analysis (Date 1 vs Date 2)**

![Comparative Period Analysis](https://github.com/Utkarsh263/Sales_Dashboard/blob/main/Screenshot%202025-11-07%20004258.png)

* Two date slicers allow comparing **two time periods**.
* Displays **Total Sales**, **Total Profit**, and **Total Units Sold** for both ranges.

---

### 🖼️ **4️⃣ Fourth Slide — Product Performance and Category Insights**

![Product Performance Insights](https://github.com/Utkarsh263/Sales_Dashboard/blob/main/Screenshot%202025-11-07%20004317.png)

* Visuals for **Top/Bottom Products** by Sales, Quantity, and Profit.
* Useful for identifying product category performance.

---

## 🧭 Tools and Technologies Used

| Tool / Feature           | Purpose                          |
| ------------------------ | -------------------------------- |
| **Power BI Desktop**     | Data modeling and visualization  |
| **Power Query**          | Data cleaning and transformation |
| **DAX**                  | Calculated columns and measures  |
| **Excel / CSV**          | Source data                      |
| **Power BI Map Visuals** | Geographic sales visualization   |

---

## 🧰 Key Features

✅ Interactive filters for Date, Product, Customer, and Promotion
✅ Dynamic comparison between any two periods
✅ Dual date table model using `USERELATIONSHIP()`
✅ Top/Bottom 5 product analysis
✅ Trend analysis by time period
✅ Profitability vs Sales correlation
✅ City-wise sales mapping

---

## 🧑‍💻 How to Use

1. Open the `.pbix` file in **Power BI Desktop**.
2. Connect your data source if required and refresh the model.
3. Use **Date Filter 1** and **Date Filter 2** to compare time periods.
4. Explore interactive visuals and slicers to gain insights.

---

## 🏁 Conclusion

This project provides a complete **data-driven sales performance dashboard**, built with:

* Robust data cleaning and transformation
* Dynamic **DAX-based dual date logic**
* Interactive and visually appealing insights

It demonstrates expertise in **Power BI**, **data modeling**, and **business intelligence storytelling** for real-world analytics.

---

## 📂 File References

| File Name                          | Description                           |
| ---------------------------------- | ------------------------------------- |
| `Screenshot 2025-11-07 004355.png` | Project Questions / Problem Statement |
| `Screenshot 2025-11-07 004217.png` | Data Table View (Slide 1)             |  
| `Screenshot 2025-11-07 004238.png` | Top/Bottom Products (Slide 2)         |
| `Screenshot 2025-11-07 004258.png` | Comparative Period Analysis (Slide 3) |
| `Screenshot 2025-11-07 004317.png` | Product Performance Visuals (Slide 4) |

---

## ✍️ Author

**Utkarsh Kohli**

---

## 📘 Disclaimer

This Power BI dashboard was created **for educational and learning purposes only**. It is intended to demonstrate skills in data analysis, visualization, and DAX modeling using sample or mock data.

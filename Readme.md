Perfect 👍 — you’ve added **DAX measures** using dual date relationships for comparative time-period analysis.
Here’s your **final professional GitHub README.md**, fully formatted for GitHub (with your DAX code, image names, and all project details).

---

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

### 1️⃣ **Top & Bottom Performing Products**

* **Top 5 / Bottom 5 Products** by Sales, Quantity, and Profit.
* Helps identify best sellers and underperforming items.

📸 *Screenshot:* `Screenshot 2025-11-07 004217.png`

---

### 2️⃣ **Detailed Data Table View**

* Interactive table displaying Customer, Product, Promotion, Date, Price, Discount, Net Sale, and Profit.
* Includes slicers for **Date, Customer Name, Product Name, and Promotion Name**.

📸 *Screenshot:* `Screenshot 2025-11-07 004238.png`

---

### 3️⃣ **Comparative Period Analysis (Date 1 vs Date 2)**

* Two date slicers to compare any time periods.
* Displays **Total Sales**, **Total Profit**, and **Total Units Sold** for both ranges.

📸 *Screenshot:* `Screenshot 2025-11-07 004258.png`

---

### 4️⃣ **Top/Bottom Product Visuals**

* Separate charts for:

  * Top 5 & Bottom 5 by Sales
  * Top 5 & Bottom 5 by Quantity
  * Top 5 & Bottom 5 by Profit

📸 *Screenshot:* `Screenshot 2025-11-07 004317.png`

---

### 5️⃣ **Comprehensive Sales Overview**

* Map visual for **Sales by City**
* KPI cards showing **Total Orders**, **Average Discount**, and **Profit vs Net Sales** correlation.
* Line chart visualizing **Sales Trends by Period (2020–2024)**

📸 *Screenshot:* `Screenshot 2025-11-07 004355.png`

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

| File Name                          | Description                       |
| ---------------------------------- | --------------------------------- |
| `Screenshot 2025-11-07 004217.png` | Top/Bottom Products               |
| `Screenshot 2025-11-07 004238.png` | Data Table View                   |
| `Screenshot 2025-11-07 004258.png` | Comparative Period Analysis       |
| `Screenshot 2025-11-07 004317.png` | Product Performance Visuals       |
| `Screenshot 2025-11-07 004355.png` | Sales by City & Summary Dashboard |

---

Would you like me to generate this README as a downloadable **`README.md` file** (ready to upload to GitHub, with markdown formatting and emojis preserved)?

# 📱 Mobile Sales Dashboard (Power BI)

This project presents a fully interactive **Power BI dashboard** built on a mobile sales dataset. The dashboard analyzes mobile phone sales performance across brands, models, cities, payment methods, customer ratings, and time periods.

It helps sales managers, regional heads, business analysts, and senior management monitor sales performance, identify top-selling products, understand customer behavior, and make better data-driven decisions.

---

## 🎯 Objectives

* Analyze overall mobile sales performance using key KPIs such as Total Sales, Total Quantity, Transactions, and Average Price.
* Identify top-performing mobile brands, models, cities, and payment methods.
* Track customer rating patterns to understand customer satisfaction.
* Monitor Month-to-Date sales performance.
* Compare current sales with the Same Period Last Year to understand year-over-year trends.
* Build a clean, interactive, and business-friendly Power BI dashboard for sales analysis.

---

## ⚙️ Data Preparation

### 🧼 Data Cleaning

* Checked the dataset for missing and inconsistent values.
* Verified column headers and corrected field names where required.
* Checked data types for important fields such as Date, Units Sold, Price Per Unit, Customer Ratings, and Transaction ID.
* Ensured sales-related columns were in proper numeric format.
* Prepared the data for dashboard-level analysis and visualization.

---

### 🔄 Data Transformation

* Created a proper **Custom Calendar Table** for time-based analysis.
* Connected the Sales Data table with the Calendar table using the Date field.
* Used date hierarchy fields such as Year, Quarter, Month, and Day.
* Created rating-based analysis using the Rating Status column.
* Prepared fields for city-wise, brand-wise, model-wise, and payment-method-wise analysis.

---

## 📈 Data Enrichment – DAX Measures

The dashboard uses DAX measures to calculate important business KPIs.

### Total Quantity

```DAX
Total_Quantity = SUM(Sales_Data[Units Sold])
```

This measure calculates the total number of mobile units sold.

---

### Total Sales

```DAX
Total_Sales =
SUMX(
    Sales_Data,
    Sales_Data[Units Sold] * Sales_Data[Price Per Unit]
)
```

This measure calculates total revenue by multiplying units sold with price per unit for each transaction.

---

### Transactions

```DAX
Transactions = COUNTROWS(Sales_Data)
```

This measure counts the total number of sales transactions.

---

### Average Price

```DAX
Average_Price = AVERAGE(Sales_Data[Price Per Unit])
```

This measure calculates the average selling price of mobile phones.

---

### Month-to-Date Sales

```DAX
MTD =
TOTALMTD(
    [Total_Sales],
    Custom_Calendar[Date].[Date]
)
```

This measure calculates sales from the start of the selected month up to the selected date.

---

### Same Period Last Year

```DAX
Same Period Last Year =
CALCULATE(
    [Total_Sales],
    SAMEPERIODLASTYEAR(Custom_Calendar[Date].[Date])
)
```

This measure compares current sales with sales from the same period in the previous year.

---

## 📊 Dashboard Overview

The dashboard consists of **three interactive pages**:

1. Dashboard
2. MTD Report
3. Same Period Last Year

---

# 🧾 1. Dashboard Page

The main dashboard page provides a high-level summary of mobile sales performance. It includes KPIs, slicers, charts, map visuals, and brand-wise analysis.

---

## 🟢 KPIs

* Total Sales
* Total Quantity
* Total Transactions
* Average Price

These KPIs give a quick overview of business performance.

---

## 🎛️ Slicers / Interactive Filters

Users can filter the dashboard by:

* Month
* Brand
* Mobile Model
* Payment Method

These slicers make the dashboard interactive and allow users to analyze sales from different business angles.

---

## 📊 Charts & Visuals

### Map Visual – Sales by City

Shows city-wise sales distribution and helps identify which locations are generating higher sales.

---

### Line Chart – Total Quantity by Month

Displays monthly sales quantity trends and helps understand sales movement over time.

---

### Funnel Chart – Ratings by Rating Status

Shows customer rating distribution based on rating status.

---

### Pie Chart – Transactions by Payment Method

Displays the share of transactions completed through different payment methods.

---

### Clustered Bar Chart – Total Sales by Mobile Model

Helps identify the best-performing mobile models based on sales revenue.

---

### Area Chart – Total Sales by Day Name

Shows sales performance across different days of the week.

---

### Table Visual – Brand-wise Performance

Displays brand-wise Total Sales and Transactions for quick comparison between mobile brands.

---

## 🔁 Page Navigation

The dashboard includes navigation buttons that allow users to move between:

* Dashboard
* MTD Report
* Same Period Last Year Report

---

# 📅 2. MTD Report Page

The MTD Report focuses on **Month-to-Date sales performance**. This page helps stakeholders track sales progress within the selected month.

---

## 🟢 KPIs

* Total Sales
* Total Quantity
* Transactions
* Average Price

---

## 🎛️ Slicers / Filters

Users can filter MTD performance by:

* Date hierarchy
* Month
* Mobile Model
* Payment Method

---

## 📊 Charts & Visuals

### Line Chart – MTD Sales Trend

Shows Month-to-Date sales movement using the MTD DAX measure.

This helps users understand how sales are progressing from the beginning of the month to the selected date.

---

## 📌 Purpose of MTD Page

The MTD page is useful for sales managers and business teams because it helps them monitor current month performance and check whether sales are moving in the right direction.

---

# 📆 3. Same Period Last Year Page

This page focuses on **year-over-year comparison** by comparing current sales with the same period from the previous year.

---

## 🟢 KPIs

* Total Sales
* Total Quantity
* Transactions
* Average Price

---

## 🎛️ Slicers / Filters

Users can filter the comparison by:

* Date hierarchy
* Month
* Mobile Model
* Payment Method

---

## 📊 Charts & Visuals

### Table Visual – Current Sales vs Same Period Last Year

Compares Total Sales with Same Period Last Year using Year and Quarter fields.

---

### Clustered Column Charts – Year-over-Year Comparison

Shows comparison between:

* Total Sales
* Same Period Last Year Sales

This helps identify whether sales have increased or decreased compared to the same period in the previous year.

---

## 📌 Purpose of Same Period Last Year Page

This page helps management understand sales growth, decline, and seasonal performance patterns by comparing current sales with past performance.

---

## 🔑 Key Insights

* The dashboard helps identify top-performing mobile models and brands.
* City-wise analysis helps understand which regions are contributing more to sales.
* Payment method analysis shows customer payment preferences.
* Customer rating analysis helps understand customer satisfaction levels.
* Month-to-Date analysis helps track current month progress.
* Same Period Last Year analysis helps compare business performance with the previous year.
* The dashboard provides a complete view of sales performance in a simple and interactive format.

---

## ✅ Conclusion

This Mobile Sales Dashboard provides a clear and interactive view of mobile sales performance. It helps business users analyze sales trends, customer behavior, payment preferences, product performance, and year-over-year growth.

By using Power BI visuals, slicers, DAX measures, and time intelligence functions, the dashboard converts raw sales data into meaningful business insights. It can support sales managers, regional heads, analysts, and senior management in making data-driven decisions.

---

## 🚀 How to Use

1. Clone this repository or download the files.
2. Open the `Mobile Sales Dashboard.pbix` file in Power BI Desktop.
3. Use slicers such as Month, Brand, Mobile Model, Payment Method, and Date to interact with the dashboard.
4. Navigate between Dashboard, MTD Report, and Same Period Last Year pages.
5. Analyze KPIs, charts, and trends to generate sales insights.

---

## 📁 Project Structure

```text
├── Mobile Sales Dashboard.pbix        # Power BI dashboard file
├── Data
│   └── Mobile Sales Data.xlsx / csv   # Mobile sales dataset
│
└── images
    └── dashboard-preview.png          # Dashboard screenshot
```

---

## 🛠 Tools Used

* Power BI Desktop – for dashboard creation and visualization
* Power Query – for data cleaning and transformation
* DAX – for calculated measures and time intelligence
* Data Modeling – for creating relationships between Sales Data and Calendar Table
* Excel / CSV Dataset – as the data source

---

## 👤 Author

**Harshdeep Singh**

LinkedIn: Add your LinkedIn profile link here
GitHub: Add your GitHub profile link here
Email: Add your email address here

---

## 🌟 Feedback & Support

Suggestions and feedback are always welcome.
If you found this project useful, please consider giving it a ⭐ on GitHub.

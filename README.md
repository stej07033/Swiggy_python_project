# 🍽️ Swiggy Sales Analysis — Python

<img width="1536" height="1024" alt="image" src="https://github.com/user-attachments/assets/a60b4fa5-6274-42d0-b75e-ad870649e71b" />

## 📌 Project Overview

This project performs **Swiggy Sales Analysis using Python** to understand sales performance, order trends, customer ratings, food categories, state-wise revenue, quarterly performance, and city-level sales.

The analysis was performed using **Pandas, NumPy, Seaborn, Matplotlib, Plotly, and Jupyter Notebook**.

The project follows a complete data-analysis workflow:

**Data Loading → Data Exploration → Data Understanding → KPI Analysis → Trend Analysis → Visualization → Business Insights**

---

# 🎯 Business Objective

The objective of this project is to analyze Swiggy food-order data and identify important business patterns related to:

* Sales revenue
* Number of orders
* Average order value
* Restaurant ratings
* Rating counts
* Monthly sales
* Daily sales
* Food category performance
* State-wise sales
* Quarterly performance
* City-wise sales

---

# 📊 Dataset Overview

The dataset contains:

* **197,430 rows**
* **10 columns**
* Data related to restaurants, locations, dishes, prices and ratings
* Order data covering **2025**

The dataset fields are:

| #  | Column          | Data Type   | Description                           |
| -- | --------------- | ----------- | ------------------------------------- |
| 1  | State           | Object      | State where the restaurant is located |
| 2  | City            | Object      | City of the restaurant                |
| 3  | Order Date      | Object/Date | Date of the order                     |
| 4  | Restaurant Name | Object      | Restaurant name                       |
| 5  | Location        | Object      | Restaurant location                   |
| 6  | Category        | Object      | Food/category classification          |
| 7  | Dish Name       | Object      | Name of the dish                      |
| 8  | Price (INR)     | Float       | Price of the ordered item             |
| 9  | Rating          | Float       | Restaurant/customer rating            |
| 10 | Rating Count    | Integer     | Number of ratings                     |

The original analysis confirms all 197,430 records are non-null across the 10 fields.

---

# 🛠️ Technologies Used

### Programming

* Python

### Libraries

* Pandas
* NumPy
* Matplotlib
* Seaborn
* Plotly

### Environment

* Jupyter Notebook

---

# 📂 Project Structure

```text
Swiggy-Sales-Analysis/
│
├── Python_Swiggy_project.ipynb
│
├── dataset/
│   └── swiggy_data_python.csv
│
├── images/
│   ├── monthly_sales.png
│   ├── daily_sales.png
│   ├── food_category_sales.png
│   ├── state_sales.png
│   ├── quarterly_sales.png
│   └── top_5_cities.png
│
├── README.md
│
└── requirements.txt
```

---

# 🔄 Project Workflow

```text
                Swiggy Dataset
                       │
                       ▼
                Import Libraries
                       │
                       ▼
                  Load Dataset
                       │
                       ▼
                Data Exploration
                       │
                       ▼
                 Data Metadata
                       │
                       ▼
                    KPIs
                       │
        ┌──────────────┼──────────────┐
        ▼              ▼              ▼
   Sales Trends   Food Analysis   Location Analysis
        │              │              │
        ▼              ▼              ▼
   Monthly/Daily   Veg vs Non-Veg   State/City Sales
        │              │              │
        └──────────────┼──────────────┘
                       ▼
                Business Insights
```

---

# 📥 Import Libraries

The project uses Pandas, NumPy, Matplotlib, Seaborn and Plotly for data analysis and visualization.

```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
import plotly.express as px

print("All libraries imported successfully!")
```

---

# 📂 Load Dataset

```python
import pandas as pd

df = pd.read_csv("swiggy_data_python.csv")

df
```

The dataset contains **197,430 rows × 10 columns**.

---

# 🔎 Exploratory Data Analysis

## First 5 Records

```python
df.head()
```

## Last 5 Records

```python
df.tail()
```

## Random Sample

```python
df.sample()
```

---

# 📋 Dataset Metadata

```python
df.shape
```

### Result

```text
(197430, 10)
```

```python
print("No of Rows:", df.shape[0])
print("No of Fields:", df.shape[1])
```

### Result

```text
No of Rows: 197430
No of Fields: 10
```

The analysis confirms 197,430 records and 10 fields.

---

# 🔤 Data Types

```python
df.dtypes
```

The dataset contains:

* 7 object columns
* 2 float columns
* 1 integer column

Specifically:

```text
State             object
City              object
Order Date        object
Restaurant Name   object
Location          object
Category          object
Dish Name         object
Price (INR)       float64
Rating            float64
Rating Count      int64
```

---

# 📊 Descriptive Statistics

```python
df.describe()
```

| Metric  | Price (INR) |  Rating | Rating Count |
| ------- | ----------: | ------: | -----------: |
| Count   |     197,430 | 197,430 |      197,430 |
| Mean    |     ₹268.51 |    4.34 |        28.32 |
| Std     |     ₹219.34 |    0.42 |        87.54 |
| Minimum |       ₹0.95 |    1.50 |            0 |
| 25%     |     ₹139.00 |    4.30 |            0 |
| 50%     |     ₹229.00 |    4.40 |            2 |
| 75%     |     ₹329.00 |    4.50 |           15 |
| Maximum |   ₹8,000.00 |    5.00 |          999 |

---

# 📌 Key Performance Indicators — KPIs

## 💰 1. Total Sales

```python
Total_sales = df["Price (INR)"].sum()

print(
    "Total Sales (INR):",
    round(Total_sales, 2)
)
```

### Result

```text
Total Sales (INR): 53,012,505.77
```

### Total Sales

**₹5.30 Crore approximately**

---

# ⭐ 2. Average Rating

```python
Average_rating = df["Rating"].mean()

print(
    "Average rating:",
    round(Average_rating, 1)
)
```

### Result

```text
Average rating: 4.3
```

---

# 🧾 3. Average Order Value

```python
Average_order_value = df["Price (INR)"].mean()

print(
    "Avg Order value (INR):",
    round(Average_order_value, 2)
)
```

### Result

```text
Avg Order value (INR): 268.51
```

---

# ⭐ 4. Total Rating Count

```python
rating_count = df["Rating Count"].sum()

print(
    "Rating Count:",
    round(rating_count, 2)
)
```

### Result

```text
Rating Count: 5,591,574
```

---

# 🛒 5. Total Orders

```python
Total_orders = df["Order Date"].count()

print(
    "Total_orders:",
    round(Total_orders, 1)
)
```

### Result

```text
Total_orders: 197430
```

---

# 📊 KPI Summary

| KPI                     |         Result |
| ----------------------- | -------------: |
| **Total Orders**        |        197,430 |
| **Total Sales**         | ₹53,012,505.77 |
| **Average Order Value** |        ₹268.51 |
| **Average Rating**      |            4.3 |
| **Total Rating Count**  |      5,591,574 |

---

# 📈 Data Visualization

The project creates multiple charts to understand Swiggy's sales performance.

---

# 📅 1. Monthly Sales Trend

The order date is converted into a datetime format and a Year-Month column is created.

```python
df["Order Date"] = pd.to_datetime(df["Order Date"])

df["YearMonth"] = (
    df["Order Date"]
    .dt.to_period("M")
    .astype(str)
)

monthly_revenue = (
    df.groupby("YearMonth")["Price (INR)"]
      .sum()
      .reset_index()
)
```

The monthly revenue trend is visualized using a line chart.

```python
plt.figure()

plt.plot(
    monthly_revenue["YearMonth"],
    monthly_revenue["Price (INR)"]
)

plt.xticks(rotation=45)
plt.xlabel("Month")
plt.ylabel("Revenue (INR)")
plt.title("Monthly Revenue Trend")

plt.tight_layout()
plt.show()
```

### 📌 Business Purpose

This visualization helps identify:

* Monthly revenue patterns
* High-performing months
* Low-performing months
* Changes in sales over time

---

# 📆 2. Daily Sales Trend

The project extracts the day of the week from the order date.

```python
df["DayName"] = (
    pd.to_datetime(df["Order Date"])
    .dt.day_name()
)
```

Daily revenue is calculated using:

```python
daily_revenue = (
    df.groupby("DayName")["Price (INR)"]
      .sum()
      .reindex([
          "Monday",
          "Tuesday",
          "Wednesday",
          "Thursday",
          "Friday",
          "Saturday",
          "Sunday"
      ])
)
```

A bar chart is then created to compare revenue across the week.

### 📌 Business Purpose

This helps understand which days generate relatively higher sales.

---

# 🥗 3. Food Category Analysis

The project classifies dishes into:

* Veg
* Non-Veg

Non-vegetarian keywords used in the analysis include:

```python
non_veg_keywords = [
    "chicken",
    "egg",
    "fish",
    "mutton",
    "prawn",
    "biryani",
    "kabad",
    "kebab",
    "non-veg",
    "non veg"
]
```

The food category is created using NumPy:

```python
df["Food Category"] = np.where(
    df["Dish Name"]
      .str.lower()
      .str.contains(
          "|".join(non_veg_keywords),
          na=False
      ),
    "Non-Veg",
    "Veg"
)
```

---

# 🥧 4. Revenue Contribution — Veg vs Non-Veg

```python
food_revenue = (
    df.groupby("Food Category")["Price (INR)"]
      .sum()
      .reset_index()
)
```

The project uses Plotly to create a donut chart:

```python
fig = px.pie(
    food_revenue,
    values="Price (INR)",
    names="Food Category",
    hole=0.5,
    title="Revenue Contribution: Veg vs Non-Veg"
)

fig.update_traces(
    textinfo="percent+label",
    pull=[0.05, 0]
)

fig.update_layout(
    height=500,
    margin=dict(
        t=60,
        b=40,
        l=40,
        r=40
    )
)

fig.show()
```

---

# 🗺️ 5. Sales by State

State-level revenue is calculated using:

```python
df.groupby(
    "State",
    as_index=False
)["Price (INR)"].sum()
```

The results are sorted from highest to lowest sales.

```python
fig = px.bar(
    df.groupby(
        "State",
        as_index=False
    )["Price (INR)"]
    .sum()
    .sort_values(
        "Price (INR)",
        ascending=False
    ),
    x="Price (INR)",
    y="State",
    orientation="h",
    title="Revenue by State (INR)"
)

fig.update_layout(
    height=600,
    yaxis=dict(
        autorange="reversed"
    )
)

fig.show()
```

### 📌 Business Purpose

This analysis helps identify:

* High-revenue states
* Regional sales performance
* Potential expansion opportunities
* Geographic differences in demand

---

# 📊 6. Quarterly Performance

The order date is converted into quarters:

```python
df["Order Date"] = pd.to_datetime(
    df["Order Date"]
)

df["Quarter"] = (
    df["Order Date"]
    .dt.to_period("Q")
    .astype(str)
)
```

The quarterly summary contains:

* Total Sales
* Average Rating
* Total Orders

```python
quarterly_summary = (
    df.groupby(
        "Quarter",
        as_index=False
    )
    .agg(
        Total_Sales=("Price (INR)", "sum"),
        Avg_Rating=("Rating", "mean"),
        Total_Orders=("Order Date", "count")
    )
    .sort_values("Quarter")
)
```

---

# 📈 Quarterly Results

| Quarter     | Total Sales (₹) | Average Rating | Total Orders |
| ----------- | --------------: | -------------: | -----------: |
| **2025 Q1** |     ₹19,667,822 |           4.34 |       73,096 |
| **2025 Q2** |     ₹19,902,257 |           4.34 |       74,163 |
| **2025 Q3** |     ₹13,442,427 |           4.34 |       50,171 |

### 🔍 Quarterly Insight

**2025 Q2** recorded the highest sales and highest number of orders among the three quarters shown in the analysis.

* Q2 Sales: **₹19.90M**
* Q1 Sales: **₹19.67M**
* Q3 Sales: **₹13.44M**

The average rating remained consistently around **4.34** across all three quarters.

---

# 🏙️ 7. Top 5 Cities by Sales

The project calculates city-level sales using:

```python
top_5_cities = (
    df.groupby("City")["Price (INR)"]
      .sum()
      .nlargest(5)
      .sort_values()
      .reset_index()
)
```

A horizontal Plotly bar chart is created:

```python
fig = px.bar(
    top_5_cities,
    x="Price (INR)",
    y="City",
    orientation="h",
    title="Top 5 Cities by Sales (INR)"
)

fig.show()
```

---

# 💡 Key Business Insights

Based on the analysis:

### 💰 Revenue

The dataset generated approximately **₹5.30 crore in total sales**.

### 🛒 Orders

The analysis contains **197,430 orders/records**.

### ⭐ Customer Ratings

The average rating is approximately **4.3**, indicating a generally high rating level in the dataset.

### 💵 Average Order Value

The average order value is approximately **₹268.51**.

### 📊 Quarterly Performance

Q2 2025 recorded the highest sales among the three quarters analyzed.

### 🗺️ Geographic Analysis

State-wise and city-wise analysis allows high-performing markets to be identified.

### 🍗 Food Category

The Veg vs Non-Veg classification provides a view of revenue contribution by food category.

---

# 📌 Business Questions Answered

### Sales Analysis

1. What is the total sales?
2. What is the average order value?
3. How many orders are present?
4. What is the monthly sales trend?
5. What is the daily sales trend?

### Rating Analysis

6. What is the average restaurant rating?
7. What is the total rating count?
8. How are ratings distributed?

### Geographic Analysis

9. Which states generate the highest revenue?
10. Which cities are the top 5 by sales?

### Food Analysis

11. What is the revenue contribution of Veg vs Non-Veg?
12. Which food category contributes more revenue?

### Time-Based Analysis

13. Which quarter has the highest sales?
14. Which quarter has the highest number of orders?
15. How does average rating change across quarters?

---

# 📸 Project Visualizations

Add the generated charts to your GitHub repository under the `images` folder.
markdown
## Monthly Revenue Trend

<img width="920" height="691" alt="image" src="https://github.com/user-attachments/assets/5bc3e953-ec68-45b8-b9b4-092f39464d5b" />

## Daily Revenue Trend

<img width="920" height="559" alt="image" src="https://github.com/user-attachments/assets/db602bda-2e45-46f7-84b9-3d6796469348" />

## Veg vs Non-Veg Revenue

<img width="920" height="708" alt="image" src="https://github.com/user-attachments/assets/772d3087-9f04-4a1b-8e00-75c3c802754b" />

## Revenue by State

<img width="920" height="850" alt="image" src="https://github.com/user-attachments/assets/ecfb9110-18ac-44de-9514-040a8c2908f7" />


## Top 5 Cities by Sales

<img width="920" height="511" alt="image" src="https://github.com/user-attachments/assets/947dd055-040d-44e4-b6de-bbe5d3c71dee" />

```

---

# 🚀 How to Run the Project

### Step 1 — Clone the Repository

```bash
git clone https://github.com/YOUR_USERNAME/Swiggy-Sales-Analysis.git
```

### Step 2 — Open the Project

```bash
cd Swiggy-Sales-Analysis
```

### Step 3 — Install Required Libraries

```bash
pip install pandas numpy matplotlib seaborn plotly jupyter
```

### Step 4 — Start Jupyter Notebook

```bash
jupyter notebook
```

### Step 5 — Open the Notebook

```text
Python_Swiggy_project.ipynb
```

Run the cells from top to bottom.

---

# 📦 requirements.txt

```text
pandas
numpy
matplotlib
seaborn
plotly
jupyter
```

---

# 🎓 Skills Demonstrated

This project demonstrates practical knowledge of:

* Python
* Pandas
* NumPy
* Data Cleaning
* Data Exploration
* Exploratory Data Analysis (EDA)
* Data Aggregation
* GroupBy
* DateTime Analysis
* KPI Creation
* Business Analysis
* Matplotlib
* Seaborn
* Plotly
* Data Visualization
* Sales Trend Analysis
* Geographic Analysis
* GitHub Project Documentation

---

# 🔮 Future Improvements

The project can be extended by integrating:

### SQL

Perform the same business analysis using MySQL/PostgreSQL.

### Power BI

Create an interactive dashboard containing:

* Total Sales
* Total Orders
* Average Order Value
* Average Rating
* Monthly Sales
* State Sales
* City Sales
* Food Category Sales

### Advanced Python

Add:

* Automated EDA
* Outlier detection
* Statistical analysis
* Predictive sales analysis
* Customer segmentation

### Interactive Dashboard

Combine:

**Python + SQL + Power BI**

to create an end-to-end Data Analyst portfolio project.

---

# 👨‍💻 Author

## SAI M

**Aspiring Data Analyst**

### Technical Skills

`Python` `SQL` `Pandas` `NumPy` `Power BI` `Excel` `Tableau` `Data Visualization`

---

# ⭐ Project Highlights

```text
197,430 Records
        ↓
Python + Pandas
        ↓
EDA & KPI Analysis
        ↓
₹53.01 Million Sales
        ↓
197,430 Orders
        ↓
4.3 Average Rating
        ↓
Monthly / Daily Analysis
        ↓
State / City Analysis
        ↓
Veg vs Non-Veg Analysis
        ↓
Quarterly Performance
```

---

## 📄 License

This project is created for **educational, learning, and Data Analyst portfolio purposes**.

** linkdin :https://www.linkedin.com/posts/madanapalli-sai-19b835389_best-free-certificate-courses-online-2025-activity-7490432956604268544-Asln?utm_source=share&utm_medium=member_android&rcm=ACoAAF-yhccBFOBRwPFDl9PAbb7jDVPGHyD_Tsc
**  Github :https://github.com/stej07033

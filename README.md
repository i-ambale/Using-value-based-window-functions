# Value-Based Window Functions in SQL

📚 **Author**: ExploreAI Academy  
⚠️ **Note**: This notebook **cannot run on Google Colab** as it relies on a **local MySQL database** connection (`united_nations`). Ensure it is run on the same local machine where **MySQL Workbench** and the **united_nations** database are installed.

---

## 🎯 Learning Objectives

In this notebook, you will learn:

- How to use the `LAG()` window function to extract values from the **previous row**.
- How to **calculate the rate of change** between consecutive values using `LAG()`.
- How to apply value-based window functions to detect **year-on-year trends**.

---

## 🗂 Overview

Value-based window functions like `LAG()` allow us to perform **comparative row analysis** by retrieving values from previous rows within a defined partition.

### 🧠 Use Case:

Track the **yearly change** in the percentage of a population with access to **managed drinking water** in each country.

---

## 🛠 Dataset & Setup

This notebook uses the `Access_to_Basic_Services` table from the `united_nations` MySQL database.  
It includes columns like:

- Country
- Year
- Access to Managed Drinking Water

> Ensure your local MySQL server is up and the database is properly configured.

---

## 🔍 Example Query Using `LAG()`

```sql
SELECT 
    Country,
    Year,
    Access_to_Water,
    LAG(Access_to_Water) OVER (PARTITION BY Country ORDER BY Year) AS Prev_Year_Access,
    (Access_to_Water - LAG(Access_to_Water) OVER (PARTITION BY Country ORDER BY Year)) AS Change
FROM Access_to_Basic_Services;
```
This query:

Retrieves the current and previous year's data.

Calculates the difference to show how access has improved or declined year-on-year.

---
## 📈 Benefits of Using LAG()
Enables trend analysis and comparative reporting.

Maintains row-level detail while analyzing temporal patterns.

Ideal for time-series data, financial changes, or progress monitoring.
---
## 🔌 Requirements
- MySQL Workbench installed and running locally

- united_nations database with relevant data

- Python environment (if running through Jupyter) with:

    - pymysql or mysql.connector
    
    - pandas
    
    - sqlalchemy (optional)
---
## 💡 Final Thoughts
Using value-based window functions such as LAG() makes SQL a powerful tool for analysing how things change over time.
Whether tracking progress or identifying negative trends, LAG() gives analysts the ability to look back—row by row.

Keep exploring! 🚀

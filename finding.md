# 🏡 Housing Sales Analysis – Objectives & Findings

This document summarizes the results of an exploratory data analysis project on property sales, using Python and pandas in a Jupyter Notebook. The dataset includes columns such as `Datesold`, `Postcode`, `Price`, `Property Type`, `Bedrooms`, and `Year`.

---

## 📥 Data Preparation

1. **Importing Libraries**  
   Imported standard libraries:
   ```python
   import numpy as np   
   import pandas as pd
   import matplotlib.pyplot as plt
   %matplotlib inline
   ```
## Basic Statistics

2. **Total Properties Sold**
    ```python
    Sales.count()
    ```
    → 28,195 records across all columns.

3. **Average House Price**
    ```python
    Sales["Price"].mean()
    ```
    → ₹608,535.33

4. **Highest Sale Price**
    ``python
    Sales["Price"].max()
    ```
    → ₹8,000,000

5. **Group Data by Year**
    ```python
    Sales_Y = Sales.groupby("Year")
    ```

6. **Group Data by Number of Bedrooms**
    ```python
    Sales_B = Sales.groupby("Bedrooms")
    ```

7. **Group Data by Property Type**
    ```python
    Sales_P = Sales.groupby("Property Type")
    ```

## Specific Queries

1. **Cheapest House Sale in 2010**
    ```python
    House_2010["Price"].min()
    ```
    → ₹110,000 (Postcode 2606, 4 bedrooms)

2. **Most Expensive House Sale in 2017**
    → ₹4,700,000 (Postcode 2603, 4 bedrooms)

3. **Most Expensive House with 5 Bedrooms Group used**
    ```python
        H_5 = House.groupby("Bedrooms").get_group(5)
        H_5["Price"].max()
    ```
    → 7300000

4. **Cheapest Unit**
    ```python
    unit_group = Sales.groupby("Property Type").get_group("unit")
    cheapest_unit = unit_group[unit_group["Price"] == unit_group["Price"].min()]
    cheapest_unit
    ```
    → 	85000 	unit 	1 	2014

5. **Cheapest Unit in 2008**
    ```python
    unit_years = unit_group.groupby("Year")
    unit_2008 = unit_years.get_group(2008)
    cheapest_unit_2008 = unit_2008[unit_2008["Price"] == unit_2008["Price"].min()]
    cheapest_unit_2008
    ```
    → 90000

6. **Average House Price in 2015**

    ```python
    Sales.groupby("Property Type").get_group("house").groupby("Year").get_group(2015)["Price"].mean()
    ```
    → 661248.3653410928

7. **Total Amount of House Sales in 2016**
    ```python
    Sales.groupby("Property Type").get_group("house").groupby("Year").get_group(2016)["Price"].sum()
    ```
    → 2,185,322,379

8. **Cheapest House Sale at Postcode 2617**
    → 240,000 for a 1-bedroom house in 2016

## Visualizations

1. **Pie Chart – Sales by Bedroom Count**
    ```python
    Axes.pie(Counts, labels=Labels, autopct="%1.1f%%", explode=[...])
    ```
    🔹 Largest slice: 3-bedroom homes – 46.1%

    
2. **Histograms of Sales Dataset**
    ```python
    Sales.hist(figsize=(14,6))
    ```

Highlights:

🔹 Peak sales in 3-bedroom category

🔹 Price range skewed toward lower values

🔹 Increased sales frequency in later years

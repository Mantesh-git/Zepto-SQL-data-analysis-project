✅ Project Overview

This project simulates how data analysts work in real-world e-commerce or retail environments using SQL. The primary focus is on handling messy inventory data, performing Exploratory Data Analysis (EDA), implementing data cleaning techniques, and writing business-driven queries to generate actionable insights.

The key objectives are:

✅ Set up a realistic e-commerce inventory database

✅ Explore product categories, availability, and pricing inconsistencies

✅ Clean the dataset by handling null values, invalid entries, and inconsistent formats

✅ Derive insights around pricing, stock availability, discounts, and revenue generation using SQL

📁 Dataset Overview

The dataset is sourced from Kaggle and mimics inventory data scraped from Zepto’s official listings. It reflects real-world challenges, such as:

Duplicate product names due to multiple SKUs for varying weights, sizes, and discounts

Missing or inconsistent values requiring data cleaning and transformation

🧾 Columns Description
Column	Description
sku_id	Unique identifier for each product entry
name	Product name as displayed in the app
category	Product category like Fruits, Snacks, Beverages, etc.
mrp	Maximum Retail Price (converted from paise to rupees)
discountPercent	Discount percentage applied on MRP
discountedSellingPrice	Final price after discount (in rupees)
availableQuantity	Units available in inventory
weightInGms	Product weight in grams
outOfStock	Boolean flag indicating if the product is out of stock
quantity	Number of units per package (may include loose produce)
🔧 Project Workflow
1️⃣ Database & Table Creation

Created a zepto table with relevant data types using PostgreSQL.

Defined sku_id as the primary key.

Ensured data consistency by specifying column constraints.

CREATE TABLE zepto (
  sku_id SERIAL PRIMARY KEY,
  category VARCHAR(120),
  name VARCHAR(150) NOT NULL,
  mrp NUMERIC(8,2),
  discountPercent NUMERIC(5,2),
  availableQuantity INTEGER,
  discountedSellingPrice NUMERIC(8,2),
  weightInGms INTEGER,
  outOfStock BOOLEAN,
  quantity INTEGER
);

2️⃣ Data Import

Imported data using \copy command in PostgreSQL.

Fixed encoding issues by saving the CSV file in UTF-8 format.

\copy zepto(category,name,mrp,discountPercent,availableQuantity,
            discountedSellingPrice,weightInGms,outOfStock,quantity)
FROM 'data/zepto_v2.csv' WITH (FORMAT csv, HEADER true, DELIMITER ',', QUOTE '"', ENCODING 'UTF8');

3️⃣ Data Exploration

Counted total records to understand dataset size.

Viewed sample records to inspect data format.

Checked for null values across columns.

Identified distinct product categories.

Compared in-stock vs out-of-stock product counts.

Analyzed SKU duplication due to different packaging and sizes.

4️⃣ Data Cleaning

Removed records where MRP or discounted price was zero.

Converted prices from paise to rupees for readability.

Handled missing or invalid entries to improve data integrity.

5️⃣ Business Insights

✅ Identified top 10 products with the best discounts

✅ Listed high-MRP products currently out of stock

✅ Estimated potential revenue by category

✅ Filtered expensive products (MRP > ₹500) with minimal discounts

✅ Ranked categories with the highest average discounts

✅ Calculated price per gram to find the most cost-effective products

✅ Grouped products into Low, Medium, and Bulk weight categories for better analysis

📈 Technologies Used

PostgreSQL (SQL)

pgAdmin for database management

Data cleaning and transformation techniques

Exploratory data analysis (EDA)

Business insight derivation using SQL queries

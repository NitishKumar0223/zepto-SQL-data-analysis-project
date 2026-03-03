# Zepto E-commerce SQL Data Analyst Portfolio Project
This is a complete, real-world data analyst portfolio project based on an e-commerce inventory dataset scraped from Zepto — one of India’s fastest-growing quick-commerce startups. This project simulates real analyst workflows, from raw data exploration to business-focused data analysis.


**📌 Project Overview**

This project simulates the workflow of a **Data Analyst** in the e-commerce industry. Using SQL, we process real-world scraped data from **Zepto** to manage inventory, clean messy datasets, and derive business-critical insights.

**Key Objectives:**

**Database Setup:** Create a robust schema for e-commerce inventory.

**EDA:** Explore product categories, pricing inconsistencies, and stock availability.

**Data Cleaning:** Handle nulls, remove invalid entries, and convert currency (Paise to Rupees).

**Business Intelligence:** Write advanced SQL queries to analyze revenue and pricing strategies.


**📁 Dataset Overview**

The dataset was sourced from [Kaggle](https://www.kaggle.com/datasets/palvinder2006/zepto-inventory-dataset/data?select=zepto_v2.csv) and was originally scraped from Zepto’s official product listings. It mimics what you’d typically encounter in a real-world e-commerce inventory system. 

Each row represents a unique SKU (Stock Keeping Unit) for a product. Duplicate product names exist because the same product may appear multiple times in different package sizes, weights, discounts, or categories to improve visibility – exactly how real catalog data looks. 

**🧾 Columns:**

**sku_id:** Unique identifier for each product entry (Synthetic Primary Key)

**name:** Product name as it appears on the app

**category:** Product category like Fruits, Snacks, Beverages, etc.

**mrp:** Maximum Retail Price (originally in paise, converted to ₹)

**discountPercent:** Discount applied on MRP

**discountedSellingPrice:** Final price after discount (also converted to ₹)

**availableQuantity:** Units available in inventory

**weightInGms:** Product weight in grams

**outOfStock:** Boolean flag indicating stock availability

**quantity:** Number of units per package (mixed with grams for loose produce) 


**🔧 Project Workflow**

**1. Database & Table Creation**
We define the structure using PostgreSQL data types:
**sql**
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
Use code with caution.

**2. Data Import**
If using the command line or facing encoding issues, use the PostgreSQL Copy Command:
**sql**
\copy zepto(category,name,mrp,discountPercent,availableQuantity,
            discountedSellingPrice,weightInGms,outOfStock,quantity)
FROM 'data/zepto_v2.csv' WITH (FORMAT csv, HEADER true, DELIMITER ',', QUOTE '"', ENCODING 'UTF8');
Use code with caution.

**3. 🔍 Data Exploration & Cleaning**
 
**Validation:** Checked for NULL values and duplicate SKUs.

**Cleaning:** Removed rows where MRP was zero.

**Transformation:** Standardized pricing by dividing Paise values by 100 to get INR.

**4. 📊 Business Insights Generated**

**Best Value:** Top 10 products by discount percentage.

**Stock Alerts:** High-MRP products currently out of stock.

**Revenue Projection:** Estimated potential revenue per category.

**Value Analysis:** Calculated price-per-gram for value-for-money items.

**Categorization:** Grouped items into Low, Medium, and Bulk weight categories.


**🛠️ How to Use**

**Clone the Repo:**
**bash**
git clone https://github.com
Use code with caution.

**Load Data:** Import the zepto_v2.csv into pgAdmin or your preferred SQL client.

**Run Analysis:** Execute the queries found in zepto_SQL_data_analysis.sql.

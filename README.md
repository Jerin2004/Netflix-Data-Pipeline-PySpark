# 📺 Netflix Data Analysis using PySpark on Databricks

This project involves analyzing the Netflix dataset using **PySpark** on **Databricks**, with data managed in **Delta Lake** format. The goal is to derive insights about Netflix's content catalog using distributed data processing.

## 🚀 Project Overview

- ✅ Technology: **Apache Spark (PySpark)**
- ✅ Platform: **Databricks**
- ✅ Storage: **Delta Lake (Databricks Delta Table)**
- ✅ Dataset: Public Netflix dataset
- ✅ Language: **Python**

## 📂 Dataset Details

The dataset includes the following key fields:
- Title
- Director
- Cast
- Country
- Date Added
- Release Year
- Rating
- Duration
- Genre (Listed In)
- Description

> Data Source: [Netflix Titles Dataset on Kaggle](https://www.kaggle.com/datasets/shivamb/netflix-shows) *(or your source if different)*

## 🛠️ Tools & Technologies Used

| Tool/Tech           | Description                                      |
|---------------------|--------------------------------------------------|
| **Databricks**      | Unified analytics platform for big data & ML     |
| **PySpark**         | Python API for Apache Spark                      |
| **Delta Lake**      | Storage layer providing ACID transactions        |
| **Apache Spark SQL**| Structured query engine for Spark                |

## 🔧 Steps Performed

1. **Data Ingestion**  
   - Loaded CSV dataset into Databricks File System (DBFS)

2. **Data Cleaning**  
   - Removed nulls and duplicates  
   - Handled data type conversions (e.g., date fields)

3. **Data Transformation**  
   - Extracted year from date fields  
   - Normalized categorical values  
   - Filtered out invalid or missing entries

4. **Delta Table Creation**  
   - Converted cleaned data into **Delta format**  
   - Registered as Delta table in Databricks for querying

5. **Analysis & Queries**  
   - Top genres by count  
   - Year-wise content release trend  
   - Country-wise distribution  
   - Content rating analysis

## 📊 Sample Queries

```python
# Example: Most frequent genres
df.select(explode(split("listed_in", ", ")).alias("genre")) \
  .groupBy("genre").count().orderBy("count", ascending=False).show()

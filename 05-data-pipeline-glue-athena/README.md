# 📊 Simple Data Pipeline Using S3, AWS Glue, and Amazon Athena

A beginner-friendly AWS data engineering project where you build a simple **serverless data pipeline** using **Amazon S3**, **AWS Glue**, and **Amazon Athena**.  
You’ll upload CSV files to S3, catalog them with Glue, and query them using standard SQL in Athena.

---

## 📌 Project Overview

In this project, you will:

1. Store raw CSV data files in an S3 bucket  
2. Use AWS Glue to automatically crawl and catalog the data  
3. Query the data using Amazon Athena with SQL  
4. Explore how serverless analytics works without managing any servers

This is a perfect first data engineering project on AWS.

---

## 🏗 Architecture Diagram (ASCII)

```flow
CSV Files (Local)
      |
      v
 Amazon S3 (Data Lake)
      |
      v
 AWS Glue Crawler (Data Catalog)
      |
      v
 AWS Glue Data Catalog (Table/Schema)
      |
      v
 Amazon Athena (SQL Queries)
```

---

## 🧰 AWS Services Used

- **Amazon S3** – Stores raw CSV data files  
- **AWS Glue** – Crawls and catalogs data into tables  
- **AWS Glue Data Catalog** – Central metadata store  
- **Amazon Athena** – Serverless SQL query engine  

---

## 🎓 What You’ll Learn

- Basics of data lakes on AWS  
- How Glue Crawlers work  
- How the Glue Data Catalog stores schema  
- Querying S3 data using Athena and SQL  
- Serverless analytics concepts  

---

## 📄 Sample CSV File (`data/sample-data.csv`)

```csv
id,name,country,sales
1,Alice,UK,1200
2,Bob,India,900
3,Charlie,USA,1500
4,Diana,UK,700
5,Edward,Canada,1100
```

---

## 🧪 Sample Athena Queries (`queries/sample-queries.sql`)

```sql
-- 1. View all data
SELECT * FROM sample_data_table LIMIT 10;

-- 2. Total sales by country
SELECT country, SUM(sales) AS total_sales
FROM sample_data_table
GROUP BY country
ORDER BY total_sales DESC;

-- 3. Filter by minimum sales
SELECT *
FROM sample_data_table
WHERE sales > 1000;
```

> Replace `sample_data_table` with the actual table name created by Glue.

---

# 🚀 Step-by-Step Deployment Guide

## **1. Upload CSV to S3**

1. Go to **Amazon S3**  
2. Create a bucket (e.g., `data-pipeline-demo-bucket`)  
3. Upload `sample-data.csv` to a folder like `raw/`

---

## **2. Create a Glue Database**

1. Go to **AWS Glue → Databases**  
2. Click **Add database**  
3. Name it (e.g., `demo_data_db`)

---

## **3. Create a Glue Crawler**

1. Go to **AWS Glue → Crawlers**  
2. Click **Add crawler**  
3. Data store: **S3**  
4. Point it to your S3 path (e.g., `s3://data-pipeline-demo-bucket/raw/`)  
5. Choose the database you created (`demo_data_db`)  
6. Run the crawler  

The crawler will create a **table** in the Glue Data Catalog.

---

## **4. Query Data Using Athena**

1. Go to **Amazon Athena**  
2. Select the database (`demo_data_db`)  
3. Select the table created by Glue  
4. Run queries like:

```sql
SELECT * FROM your_table_name LIMIT 10;
```

5. Use the sample queries from `queries/sample-queries.sql`

---

# 🧪 Testing Checklist

- Glue Crawler successfully creates a table  
- Athena can query the table without errors  
- Aggregations (SUM, GROUP BY) work correctly  
- Data matches the CSV content  

---

# 💡 Optional Enhancements

- Add more CSV files (partitioned by date or country)  
- Use Glue ETL jobs to transform data  
- Store transformed data in a `processed/` S3 folder  
- Visualize Athena results in Amazon QuickSight  
- Add IAM policies for fine-grained access control  

---
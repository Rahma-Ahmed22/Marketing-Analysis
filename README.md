# **Marketing Analytics Dashboard – ShopEasy**

## **Project Overview**

This project analyzes marketing performance and customer behavior for **ShopEasy**, an online retail company experiencing declining engagement and conversion rates despite increased marketing spending.

The goal of the project was to build a **complete marketing analytics pipeline** that transforms raw data into actionable business insights. The workflow combines **SQL for data preparation, Python for sentiment analysis, and Power BI for data visualization** to identify key opportunities for improving customer engagement and conversion performance.

The final output is an **interactive marketing analytics dashboard** that highlights conversion bottlenecks, marketing campaign effectiveness, customer sentiment trends, and product performance.

---

# **Project Objectives**

ShopEasy faced several business challenges:

* Declining **customer engagement**
* Reduced **conversion rates**
* Increasing **marketing costs with lower ROI**
* Lack of insights into **customer feedback and satisfaction**

The objective of this project was to:

* Analyze the **customer journey and conversion funnel**
* Evaluate **marketing campaign engagement**
* Perform **sentiment analysis on customer reviews**
* Identify **key drivers of purchases and drop-offs**
* Provide **data-driven strategic recommendations**

---

# **Tools & Technologies**

* **SQL Server** – Data extraction, transformation, and cleaning
* **Python (Pandas, NLTK, VADER)** – Sentiment analysis of customer reviews
* **Power BI** – Data modeling and interactive dashboard development
* **DAX** – KPI calculations and performance metrics

---

# **Project Workflow**

The project followed a **three-stage analytics pipeline**:

1. **Data Preparation with SQL**
2. **Sentiment Analysis with Python**
3. **Interactive Dashboard Development with Power BI**

---

# **Step 1 – Data Extraction & Cleaning (SQL)**

The project began with loading and preparing data in **SQL Server**. Several datasets were used, including:

* Customer data
* Product information
* Customer journey interactions
* Marketing engagement data
* Customer reviews

SQL was used to perform **data extraction, transformation, and cleaning** before analysis.

---

## **Customer Data Enrichment**

Customer information was enriched by joining customer records with geographic data.

A **LEFT JOIN** was used to combine the `customers` table with the `geography` table to include:

* Country
* City

This enrichment enabled **geographic customer segmentation** for later analysis.

---

## **Product Data Transformation**

Product prices were categorized into **price tiers** using a SQL `CASE` statement.

Products were grouped into:

* **Low price products** (< $50)
* **Medium price products** ($50 – $200)
* **High price products** (> $200)

This transformation helped analyze **conversion performance across pricing segments**.

---

## **Marketing Engagement Data Cleaning**

Marketing engagement data required multiple cleaning steps.

Key transformations included:

* Standardizing content type values using `UPPER()`
* Fixing inconsistent labels (e.g., *Socialmedia → Social Media*)
* Splitting combined metrics (**ViewsClicksCombined**) into separate **Views** and **Clicks**
* Formatting engagement dates
* Removing irrelevant marketing channels such as **Newsletter**

These steps ensured consistent metrics for **engagement performance analysis**.

---

## **Customer Journey Data Cleaning**

Customer journey data was processed to ensure high data quality.

### **Duplicate Detection**

A **Common Table Expression (CTE)** with `ROW_NUMBER()` was used to detect duplicate records.

Duplicates were defined based on identical combinations of:

* CustomerID
* ProductID
* VisitDate
* Stage
* Action

Only the **first occurrence of each duplicate group** was kept.

---

### **Handling Missing Data**

Missing duration values were replaced using the **average duration for each visit date** using the `COALESCE()` function.

This allowed interaction duration to remain usable for behavioral analysis.

---

### **Data Standardization**

Customer journey stage values were standardized using:

`UPPER(Stage)`

This ensured consistent stage naming across the dataset.

---

# **Step 2 – Sentiment Analysis (Python)**

Customer reviews were analyzed using **Natural Language Processing (NLP)** techniques.

Python was used to perform sentiment analysis on review text using the **VADER Sentiment Analyzer from NLTK**.

---

## **Data Extraction**

Customer reviews were extracted from the SQL database using **pyodbc** and loaded into a **Pandas DataFrame**.

The dataset included:

* Review ID
* Customer ID
* Product ID
* Rating
* Review Text
* Review Date

---

## **Sentiment Score Calculation**

The VADER model was used to generate a **compound sentiment score** for each review.

Scores range between:

* **-1 → Strongly Negative**
* **0 → Neutral**
* **+1 → Strongly Positive**

---

## **Sentiment Categorization**

Sentiment was classified using both:

* Review text sentiment score
* Customer rating

Categories included:

* Positive
* Mixed Positive
* Mixed Negative
* Negative
* Neutral

This hybrid classification improved the accuracy of sentiment interpretation.

---

## **Sentiment Bucketing**

Sentiment scores were grouped into ranges for visualization:

* **0.5 to 1.0 → Strong Positive**
* **0.0 to 0.49 → Mild Positive**
* **-0.49 to 0.0 → Mild Negative**
* **-1.0 to -0.5 → Strong Negative**

The processed dataset was exported as a **CSV file** for use in Power BI.

---

# **Step 3 – Dashboard Development (Power BI)**

The cleaned and enriched datasets were imported into **Power BI** to build an interactive marketing analytics dashboard.

The dashboard uses a **custom dark analytics theme** to improve visual clarity and create a modern design suitable for portfolio presentation.

---

## **Dashboard Structure**

The dashboard consists of several analytical sections:

* **Executive Overview**
* **Conversion Funnel Analysis**
* **Marketing Engagement Analysis**
* **Customer Feedback & Sentiment**
* **Product Performance**

---

## **Key Performance Indicators (KPIs)**

Several KPIs were calculated using **DAX** measures, including:

* Conversion Rate
* Customer Engagement Rate
* Average Order Value (AOV)
* Customer Feedback Score
* Total Visitors
* Total Purchases

These metrics provide a high-level view of marketing and customer performance.

---

# **Key Insights**

## **Conversion Funnel Performance**

* Overall conversion rate: **11.4%** (198 purchases from 1,737 homepage visitors)
* Largest drop-off occurs between **Product Page → Checkout** (45.5%)
* Checkout abandonment rate: **74.4%**

Reducing checkout abandonment by **20% could generate approximately 115 additional purchases** without increasing traffic.

---

## **Product & Pricing Insights**

* Low-price products convert **2.6x higher** than high-price products.
* Average conversion rate:

  * Low-price products: **18.2%**
  * High-price products: **6.9%**

Top performing products:

* Running Shoes
* Fitness Tracker
* Yoga Mat
* Basketball
* Soccer Ball

---

## **Marketing Engagement Insights**

* **Social media content** has the highest engagement rate at **28%**.
* Engagement from blogs and videos averages **10–12%**.
* Campaigns **11 and 18** show the highest click-through rates.

Engagement rates declined from **39.4% (Jan 2024)** to **11.2% (Sep 2025)**, indicating potential **campaign fatigue**.

---

## **Customer Sentiment Insights**

* Average customer rating: **3.69 / 5**
* Only **30% of reviews are strongly positive**.
* **35% of reviews mention price concerns**, indicating price sensitivity.

Positive sentiment drivers:

* Product quality
* Customer support

Negative sentiment drivers:

* Price perception
* Product expectations not met

---

# **Strategic Recommendations**

Based on the analysis, several data-driven recommendations were identified:

**Reduce checkout abandonment**

Adding trust badges, payment security indicators, and simplified checkout flows could recover **115+ additional purchases**.

**Prioritize social media marketing**

Reallocate marketing budget toward social media channels due to **2.3x higher engagement rates**.

**Address price perception**

Introduce **tiered pricing or lower-cost product versions** for premium items.

**Increase Average Order Value**

Implement **product bundling and cross-sell strategies** to increase AOV by an estimated **$50–$100 per transaction**.

---

# **Project Outcome**

This project demonstrates a full **end-to-end marketing analytics workflow**, from raw data preparation to advanced analysis and visualization.

The analysis provides actionable insights that help improve:

* Marketing effectiveness
* Customer engagement
* Conversion performance
* Customer satisfaction

The final dashboard serves as a **decision-support tool for marketing and e-commerce teams**, enabling data-driven optimization of campaigns, pricing strategies, and customer experience.

# Marketing-Analysis

1️⃣ #Project Summary 
Marketing Analytics Dashboard – ShopEasy

This project analyzes marketing performance and customer behavior for ShopEasy, an online retail company experiencing declining engagement and conversion rates despite increased marketing spending.

The analysis combines SQL, Python, and Power BI to build a complete marketing analytics pipeline.

The workflow included:

SQL for data extraction, transformation, and cleaning
Python (NLP) to perform sentiment analysis on customer reviews
Power BI to build an interactive marketing analytics dashboard
Funnel analysis, engagement analytics, and customer sentiment insights to identify improvement opportunities.

The final dashboard reveals conversion bottlenecks, marketing campaign effectiveness, customer sentiment trends, and product performance, enabling actionable business recommendations.

Key insights include identifying checkout abandonment as the biggest revenue loss point, higher engagement from social media campaigns, price sensitivity in product feedback, and seasonal variations in conversion performance.

2️⃣ Detailed Project Walkthrough
Project Objective

ShopEasy launched several marketing campaigns but observed:

Reduced customer engagement
Declining conversion rates
Increasing marketing expenses
Mixed customer feedback

The goal of this project was to analyze the full customer journey, marketing engagement, and customer feedback to identify opportunities for improving conversion and marketing effectiveness.

Step 1 — Data Extraction and Preparation (SQL)

The project started by extracting and preparing data from a SQL Server database.

SQL was used to perform:

Data extraction
Data transformation
Data cleaning
Data standardization
Feature engineering

The data consisted of the following datasets:

Customer information
Product details
Customer journey interactions
Marketing engagement data
Customer reviews
Customer Data Enrichment

Customer records were enriched by joining customer data with geographic information.

A LEFT JOIN was used to combine customer attributes with their corresponding country and city information.

This allowed the analysis to include geographic customer segmentation.

Operations performed:

Customer demographic extraction
Geographic enrichment
Data integration between tables
Product Feature Engineering

Product pricing was transformed into price categories using a SQL CASE statement.

Products were categorized into:

Low price products (< $50)
Medium price products ($50–$200)
High price products (> $200)

This feature was later used to analyze conversion behavior across price segments.

Marketing Engagement Data Cleaning

Engagement data required several cleaning steps:

Data transformations included:

Standardizing content types using UPPER() formatting
Correcting inconsistent labels such as "Socialmedia" → "Social Media"
Splitting combined metrics (ViewsClicksCombined) into separate Views and Clicks fields
Formatting engagement dates for consistency
Removing irrelevant marketing channels such as Newsletter

These steps ensured the dataset was ready for engagement analysis and campaign performance evaluation.

Customer Journey Data Cleaning

Customer journey data was processed to ensure data quality and reliability.

Several data quality checks were performed:

Duplicate Detection

A Common Table Expression (CTE) combined with ROW_NUMBER() was used to identify duplicate records.

Duplicates were defined as records sharing the same:

CustomerID
ProductID
VisitDate
Stage
Action

Only the first occurrence was retained to prevent double counting.

Handling Missing Values

Missing duration values were replaced using the average duration per date with the COALESCE() function.

This ensured interaction duration remained usable for behavioral analysis.

Data Standardization

Customer journey stages were standardized using:

UPPER(Stage)

This ensured consistency across funnel stage names.

Step 2 — Sentiment Analysis (Python)

To better understand customer feedback, Natural Language Processing (NLP) was applied using Python.

The sentiment analysis process included:

Extracting customer reviews from SQL Server
Processing review text using NLTK's VADER sentiment analyzer
Generating sentiment scores
Categorizing sentiment using both review text and rating values
Sentiment Score Calculation

Each review was analyzed using the VADER sentiment model, which produces a compound sentiment score between -1 and 1.

Score interpretation:

Positive sentiment → closer to 1
Neutral sentiment → near 0
Negative sentiment → closer to -1
Sentiment Categorization

Sentiment categories were determined using both:

Sentiment score
Customer rating

Categories included:

Positive
Mixed Positive
Mixed Negative
Negative
Neutral

This hybrid approach allowed more accurate interpretation of customer opinions.

Sentiment Bucketing

Sentiment scores were grouped into buckets for easier visualization:

0.5 to 1.0 → Strong positive sentiment
0.0 to 0.49 → Mild positive sentiment
-0.49 to 0.0 → Mild negative sentiment
-1.0 to -0.5 → Strong negative sentiment

The enriched dataset was exported as a CSV file and used for dashboard analysis.

Step 3 — Data Visualization and Analytics (Power BI)

The final stage involved building an interactive marketing analytics dashboard in Power BI.

The dashboard was designed using a custom dark analytics theme and organized into multiple analytical views.

Dashboard sections included:

Executive overview
Conversion funnel analysis
Marketing engagement analysis
Customer feedback and sentiment analysis
Product performance analysis
Key Performance Indicators

Several KPIs were calculated to evaluate marketing performance.

These included:

Conversion Rate
Customer Engagement Rate
Average Order Value (AOV)
Customer Feedback Score
Total Visitors
Total Purchases

These metrics provided a high-level overview of marketing effectiveness and customer behavior.

Conversion Funnel Analysis

A conversion funnel was constructed to analyze the customer journey stages:

Homepage → Product Page → Checkout → Purchase

This allowed the identification of drop-off points in the purchasing process.

The analysis revealed significant abandonment at the checkout stage, highlighting a key revenue opportunity.

Marketing Engagement Analysis

Marketing engagement was analyzed across different content formats:

Social Media
Blog Content
Video Content

Metrics analyzed included:

Views
Clicks
Likes
Engagement rate

This analysis helped identify which marketing channels were most effective at driving interaction.

Customer Sentiment Analysis

Customer feedback was analyzed using:

Sentiment score distribution
Review ratings
Frequent feedback themes

This allowed the identification of common customer satisfaction drivers and friction points.

Key Insights from the Analysis
Conversion Funnel Performance

The overall conversion rate from homepage to purchase is 11.4%, significantly above the retail average of 2–5%.

However, checkout abandonment remains the largest loss point, with 74.4% of checkout visitors failing to complete their purchase.

Reducing checkout abandonment by just 20% could generate an estimated 115 additional purchases without increasing traffic.

Product Pricing Insights

Lower-priced products convert significantly better.

Products priced under $50 convert at 18.2%, compared to just 6.9% for high-priced products.

This suggests price sensitivity among customers.

Marketing Engagement Insights

Social media content generates the highest engagement rate at 28%, more than double the engagement of blog and video content.

However, engagement rates have declined over time, indicating campaign fatigue after 12–18 months.

Customer Sentiment Insights

The average customer feedback score is 3.69 out of 5, below the retail benchmark of 4.2.

Many reviews mention good product quality but high prices, highlighting price perception as a key friction point.

Strategic Recommendations

Based on the analysis, several strategic recommendations were proposed.

Improving checkout trust signals (payment badges, guarantees, and simplified forms) could significantly reduce abandonment.

Marketing investment should prioritize social media channels, which generate significantly higher engagement.

Introducing tiered pricing or lower-cost alternatives could address price sensitivity among customers.

Product bundling strategies could increase the average order value by $50–100 per transaction.

Tools Used

SQL Server
Python (Pandas, NLTK, VADER Sentiment Analysis)
Power BI
Data Modeling and Visualization

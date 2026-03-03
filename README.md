# SQL-RFM  
Snowflake SQL Customer Segmentation (RFM)     
**Project Goal**    
To identify high-value customers, understand purchasing behavior, and segment the user base for targeted marketing strategies. This analysis provides actionable insights to prevent customer churn and maximize revenue from top-tier buyers.   
**Tools & Technologies**    
Snowflake Data Warehouse: Connected to the TPCH_SF1 sample database.SQL: Advanced querying using Common Table Expressions (CTEs), Aggregate Functions (MAX, SUM, AVG, COUNT), Window Functions (MEDIAN), and multi-table JOINs.
**The Process & Logic**    
I chose to use a CASE-based approach for RFM Scores using medians instead of NTILE, not just to keep things simple, but because it actually made more sense for the skewed data.
**Data Aggregation:**    
Built a customer-level base table by joining ORDERS, CUSTOMER, and NATION tables.  
**RFM Value Calculation:**     
Recency: Days since the last order. I weighted Recency as the most critical factor for customer vitality.Frequency: Total count of orders per customer.Monetary: Total amount spent by the customer.  
**Custom Scoring System:**  
Recency Score: Grouped into logical business buckets: Last Month (1), Last Quarter (2), Last Year (3), and Inactive/Lost (4).  
**Frequency & Monetary Scores:**  
Calculated the Medians and Quartiles (Q1, Q3) to rank customers from 1 (Highest) to 4 (Lowest) without being skewed by extreme outliers.Segmentation: Combined scores (ranging from 3 to 12) to categorize users into 5 actionable segments: Champion, Loyal, Potential, At Risk, and Churned.  
**Key Business Insights**  
The "_Potential_" segment drives the most revenue (~90.8B): This is the largest user group (36,918 customers). They are currently average but have massive room for growth.   
Recommendation: Nurture with retention strategies to push them toward "Loyal" status rather than letting them slip to "At Risk".  
"_At Risk_" customers hold significant capital (~41.1B): Over 27,000 customers are showing a drop in activity.   
Recommendation: Deploy targeted re-engagement campaigns (reminders, special offers) to prevent churn.  
"_Champions_" are rare but highly valuable (~6.5B): Only 1,385 customers make up this top tier, but their per-customer spend is massive.   
Recommendation: Provide VIP treatment and exclusive perks to maximize Lifetime Value (LTV).  
**Global VIP Distribution:**   
Germany, France, and the United States house the highest total count of "Champion" customers  
  

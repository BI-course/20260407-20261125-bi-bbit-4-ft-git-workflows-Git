# Warehouse Schema Design: Star Schema for Business Analytics

## 1. Overview
Based on the **Data Source Review**, this document outlines a Star Schema design optimized for a centralized Data Warehouse. This schema integrates internal operational data (CRM, ERP, IoT) with external market insights (APIs, Web Scraping) to provide a holistic view of business performance.

## 2. Star Schema Architecture
The schema follows a "Star" pattern with a central **Fact Table** containing quantitative metrics and surrounding **Dimension Tables** containing descriptive attributes.

[Image of a star schema diagram for a retail business]

### 2.1 Fact Table: `Fact_Sales_Performance`
This table captures transactional events enriched with environmental context (e.g., weather and market trends).

| Column Name | Data Type | Description | Source Reference |
|:---|:---|:---|:---|
| `Sale_ID` (PK) | BIGINT | Unique identifier for the transaction. | CRM / POS System |
| `Date_Key` (FK) | INT | Link to `Dim_Date`. | Internal System |
| `Customer_Key` (FK) | INT | Link to `Dim_Customer`. | CRM (Salesforce/HubSpot) |
| `Product_Key` (FK) | INT | Link to `Dim_Product`. | ERP (SAP/Oracle) |
| `Location_Key` (FK) | INT | Link to `Dim_Location`. | Internal / IoT Sensors |
| `Employee_Key` (FK) | INT | Link to `Dim_Employee`. | Jira / Timesheets |
| `External_Market_Key` (FK) | INT | Link to `Dim_External_Conditions`. | Third-Party APIs |
| `Quantity` | INT | Number of units sold. | Transactional Database |
| `Gross_Revenue` | DECIMAL | Total revenue before discounts. | Transactional Database |
| `Net_Revenue` | DECIMAL | Revenue after discounts/returns. | Transactional Database |
| `Customer_Sentiment_Score` | FLOAT | Derived sentiment from product reviews. | Web Scraping (External) |

---

## 3. Dimension Tables

### 3.1 `Dim_Customer` (Internal + External Enrichment)
A "Customer 360" view merging internal profile data with external social/demographic data.

| Column Name | Description | Source |
|:---|:---|:---|
| `Customer_Key` (PK) | Surrogate Key. | Internal |
| `Customer_ID` | Original CRM ID. | CRM |
| `Name` | Customer full name. | CRM |
| `Segment` | Enterprise, SMB, or Consumer. | Internal Analysis |
| `Social_Influence_Tier` | Category based on external presence. | LinkedIn/Twitter API |
| `Credit_Score_Range` | Financial health indicator. | Data Marketplaces (Experian) |

### 3.2 `Dim_Product` (Internal)
Details regarding items sold, managed through the ERP system.

| Column Name | Description | Source |
|:---|:---|:---|
| `Product_Key` (PK) | Surrogate Key. | Internal |
| `SKU` | Stock Keeping Unit. | ERP |
| `Category` | Electronics, Clothing, etc. | ERP |
| `Unit_Cost` | Internal manufacturing/purchase cost. | ERP / Supply Chain |
| `Supplier_Name` | Name of the primary vendor. | Partner Data |

### 3.3 `Dim_Location` (Internal + IoT)
Physical or digital sales points, including physical sensor data.

| Column Name | Description | Source |
|:---|:---|:---|
| `Location_Key` (PK) | Surrogate Key. | Internal |
| `Store_ID` | Branch or Digital Store ID. | POS System |
| `City / Region` | Geographic location. | Internal |
| `Warehouse_Temp_Avg` | Average temp during storage. | IoT Hardware Sensors |
| `Foot_Traffic_Index` | Local area busy-ness. | Third-Party APIs |

### 3.4 `Dim_External_Conditions` (External)
Captures the "Why" behind performance fluctuations using external data.

| Column Name | Description | Source |
|:---|:---|:---|
| `Condition_Key` (PK) | Surrogate Key. | Internal |
| `Weather_Event` | Rain, Snow, Heatwave. | Weather API |
| `Competitor_Price_Index` | Market pricing vs Internal. | Web Scraping |
| `Market_Volatility` | Financial market status. | Financial APIs |

---

## 4. Implementation Logic
1.  **ETL/ELT Process**: 
    -   Internal data is pulled via batch (SQL) or streaming (App Logs).
    -   External data is fetched via REST APIs or Scrapers.
2.  **Data Cleaning**: 
    -   Address inconsistencies in schema changes (referenced in Source Review 2.2).
    -   Validate external API data against internal totals (referenced in 3.2).
3.  **Governance**: 
    -   PII (Names, Emails) in `Dim_Customer` must be masked according to GDPR/CCPA.

## 5. Summary of Integration
This Star Schema directly addresses the **Hybrid/Derived Sources** identified in the data review. By linking the `Fact_Sales_Performance` table to both internal (Product, Employee) and external (Market Conditions) dimensions, the business can perform advanced correlations, such as:
- *How did external weather events impact sales in locations where IoT sensors reported high warehouse humidity?*
- *Is there a correlation between competitor pricing (Scraped) and our Net Revenue?*
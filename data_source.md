# Data Source Review: Internal and External Data in a Business

## 1. Objective
This document reviews the primary sources of data within a typical business environment. The goal is to categorize, evaluate, and document where data originates to support analytics, decision-making, and system integration.

## 2. Internal Data Sources
Internal data is generated directly from the company’s own operations, systems, and users. It is generally more structured and accessible.

| Source Category | Examples | Typical Use Case |
|----------------|----------|------------------|
| **Transactional Databases** | CRM (Salesforce, HubSpot), ERP (SAP, Oracle), POS systems | Sales forecasting, customer lifetime value, inventory management |
| **Application Logs** | Web server logs, API logs, application error logs | Performance monitoring, debugging, user behavior analysis |
| **Internal Documents** | Spreadsheets (Excel/Sheets), internal wikis, reports | Ad-hoc analysis, manual reporting, knowledge management |
| **Employee-Generated Data** | Timesheets, expense reports, project management tools (Jira, Asana) | Resource allocation, cost accounting, productivity metrics |
| **IoT & Hardware Sensors** | Warehouse scanners, manufacturing sensors, office access logs | Supply chain optimization, predictive maintenance, security |

### 2.1 Strengths of Internal Data
- High relevance to business-specific questions.
- More control over quality, governance, and schema.
- No external procurement cost.

### 2.2 Weaknesses
- May be siloed across departments (e.g., sales vs. marketing).
- Historical data can have inconsistencies due to schema changes.
- Requires data engineering to centralize (e.g., data warehouse/lake).

## 3. External Data Sources
External data originates outside the company but can enrich internal insights.

| Source Category | Examples | Typical Use Case |
|----------------|----------|------------------|
| **Third-Party APIs** | Weather, traffic, financial market data, social media APIs (Twitter, LinkedIn) | Supply chain risk, demand forecasting, sentiment analysis |
| **Public Datasets** | Government statistics (census, labor), economic indicators, open data portals | Market sizing, competitor benchmarking, regulatory compliance |
| **Web Scraping** | Competitor prices, product reviews, job postings | Dynamic pricing, reputation monitoring, talent market analysis |
| **Data Marketplaces** | Snowflake Marketplace, AWS Data Exchange, D&B, Experian | Customer enrichment, fraud detection, lead scoring |
| **Partner/Supplier Data** | Distributor inventory, logistics provider tracking, co-marketing analytics | Vendor scorecards, joint business planning, channel optimization |

### 3.1 Strengths of External Data
- Provides context beyond internal operations (e.g., market trends).
- Enables predictive models without historical lag (e.g., real-time weather).
- Useful for validating internal hypotheses.

### 3.2 Weaknesses
- Often costly (subscription fees, API limits).
- Legal/compliance risks (GDPR, CCPA, terms of service violations).
- Data quality varies; requires validation and cleaning.

## 4. Hybrid / Derived Sources
Some data sources blend internal and external origins or are derived through transformation.

- **Customer 360 view**: Merge CRM (internal) with social media profiles (external).
- **Enriched logs**: Web analytics (internal IP, user agent) + geolocation databases (external).
- **Benchmarking reports**: Internal KPI + industry aggregate data from associations.

## 5. Key Considerations for Selection
When choosing or prioritizing data sources:

- **Business value**: Does it directly impact a KPI (revenue, cost, risk)?
- **Data freshness**: Real-time? Batch (daily/hourly)? Historical only?
- **Volume & velocity**: GB/TB per day? Streaming or static?
- **Governance & privacy**: PII? Cross-border transfer restrictions?
- **Cost of integration**: Engineering time, storage, licensing, maintenance.

## 6. Recommended Next Steps
1. **Inventory existing data sources** – interview domain owners (Sales, Ops, IT).
2. **Classify by sensitivity** – PII, confidential, public.
3. **Assess data quality** – completeness, accuracy, timeliness.
4. **Define ingestion priority** – quick wins vs. strategic long-term.
5. **Document lineage** – source → transformation → destination → usage.

## 7. Conclusion
A modern business relies on a mix of internal transaction systems, application logs, and external APIs/public data. The key to leveraging them effectively is not collecting everything, but aligning data source selection with measurable business outcomes and operational constraints.


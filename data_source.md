# Data Sources in Business Intelligence

## Overview
Data sources are the origin points of raw data that feed into a 
Business Intelligence system. Understanding them is critical for 
designing effective data pipelines and choosing the right tools 
for extraction and transformation.

## Primary Data Source Categories

### 1. Transactional Databases (OLTP)
Operational databases such as MySQL, PostgreSQL, and Oracle that 
record day-to-day business transactions. Examples include sales 
records, inventory updates, and customer orders.

### 2. Flat Files
Structured or semi-structured files such as CSV, Excel, and JSON 
that are exported from various departments or third-party systems. 
Common in legacy systems and manual reporting workflows.

### 3. APIs
Application Programming Interfaces that allow real-time or 
scheduled data retrieval from external platforms such as 
Google Analytics, Salesforce, or social media platforms.

### 4. Streaming Sources
Continuous, real-time data feeds from IoT devices, clickstreams, 
or event logs. Tools like Apache Kafka are commonly used to 
ingest and process this type of data.

## Summary
Each source type has different latency, volume, and formatting 
characteristics that directly influence the design of the 
data pipeline and the choice of BI tools.

# Star Schema Quality Validation

## Overview
This document outlines the Data Quality checks required for the Star Schema architecture defined in `warehouse_schema.md`. As the Quality Lead, these constraints ensure that our BI reports remain accurate and trustworthy.

## 1. Referential Integrity (The Most Critical Rule)
Every Foreign Key in the **Fact Table** (e.g., `Customer_ID`, `Product_ID`) MUST have a matching Primary Key in the corresponding **Dimension Table**. If a sale is recorded for a `Product_ID` that does not exist in the Product Dimension, the data pipeline must flag it as an error.

## 2. Uniqueness Constraint
The Primary Keys within all **Dimension Tables** (Time, Product, Customer, Location) must be 100% unique. Duplicate keys will cause double-counting in the Fact Table and ruin revenue calculations.

## 3. Completeness (No-Null Rule)
Foreign keys in the **Fact Table** cannot be NULL. If a transaction occurs, we must know the Time, Location, and Product. If any of these are missing, the data is incomplete and should be quarantined.

## Conclusion
By enforcing these three rules, we ensure the structural integrity of our BI data warehouse.

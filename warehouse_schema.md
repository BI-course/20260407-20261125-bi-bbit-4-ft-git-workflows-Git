# Star Schema

## Overview
A Star Schema is a data warehouse design model used in Business Intelligence systems. It organizes data into a central fact table connected to multiple dimension tables. The structure resembles a star, which is where it gets its name.

---

## Structure of a Star Schema

### 1. Fact Table
The fact table is the central table in the schema. It contains quantitative data (measurable values) and foreign keys that link to dimension tables.

**Examples of measures:**
- Sales amount
- Quantity sold
- Revenue

---

### 2. Dimension Tables
Dimension tables store descriptive information that provides context to the data in the fact table.

**Examples of dimensions:**
- **Time** (date, month, year)
- **Product** (name, category, price)
- **Customer** (name, location)
- **Location** (city, region, country)

---

## Example of Star Schema

A sales data warehouse may include:

- **Fact Table:** Sales  
- **Dimension Tables:** Customer, Product, Time, Location  

This allows queries such as:
> “What is the total sales of a product in a specific region over time?”

---

## Advantages of Star Schema

- Simple and easy to understand  
- Fast query performance due to fewer joins  
- Optimized for reporting and analytics  
- Widely supported in BI tools  

---

## Disadvantages of Star Schema

- Data redundancy in dimension tables  
- Not ideal for complex relationships  
- Can require more storage space  

---

## Use in Business Intelligence

Star Schema is commonly used in data warehouses to support:
- Reporting  
- Dashboards  
- Data analysis  

It enables efficient querying and helps organizations make data-driven decisions.

---

## Conclusion
The Star Schema is a fundamental data modeling technique in Business Intelligence. Its simplicity and performance make it a preferred choice for designing data warehouses, especially for analytical and reporting purposes.
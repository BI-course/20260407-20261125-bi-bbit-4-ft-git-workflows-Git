# Warehouse Schema – Star Schema Design

## 1. Overview

A Star Schema is a way of organizing data in a data warehouse.

It consists of:

* A Fact Table - stores numerical data like sales, quantities
* Dimension Tables - store descriptive details

It is called a star schema because the structure looks like a star.

---

## 2. Purpose

The star schema is used to:

* Make data easy to understand
* Improve query performance
* Support reporting and dashboards
* Help in business analysis

---

## 3. Schema Structure

### 3.1 Fact Table

The fact table stores measurable data and connects to dimension tables using foreign keys.

**Example: `Sales_Fact`**

| Column Name      | Description             |
| ---------------- | ----------------------- |
| sale_id (PK)     | Unique ID for each sale |
| product_id (FK)  | Links to Product table  |
| customer_id (FK) | Links to Customer table |
| time_id (FK)     | Links to Time table     |
| store_id (FK)    | Links to Store table    |
| quantity_sold    | Number of items sold    |
| total_amount     | Total revenue from sale |

---

### 3.2 Dimension Tables

#### Product Dimension (`Product_Dim`)

| Column Name     | Description      |
| --------------- | ---------------- |
| product_id (PK) | Product ID       |
| product_name    | Name of product  |
| category        | Product category |
| brand           | Brand name       |

#### Customer Dimension (`Customer_Dim`)

| Column Name      | Description       |
| ---------------- | ----------------- |
| customer_id (PK) | Customer ID       |
| customer_name    | Name of customer  |
| gender           | Gender            |
| age_group        | Age group         |
| location         | Customer location |

#### Time Dimension (`Time_Dim`)

| Column Name  | Description |
| ------------ | ----------- |
| time_id (PK) | Time ID     |
| date         | Full date   |
| day          | Day         |
| month        | Month       |
| quarter      | Quarter     |
| year         | Year        |

#### Store Dimension (`Store_Dim`)

| Column Name   | Description |
| ------------- | ----------- |
| store_id (PK) | Store ID    |
| store_name    | Store name  |
| city          | City        |
| region        | Region      |

---

## 4. Diagram

```
            Product_Dim
                 |
Customer_Dim — Sales_Fact — Time_Dim
                 |
             Store_Dim
```

---

## 5. Key Characteristics

* Simple structure
* Easy to query
* Fast performance
* Good for analysis

---

## 6. Advantages

* Easy to understand
* Fast queries
* Works well with BI tools

---

## 7. Disadvantages

* Data redundancy (data may be repeated)
* Not ideal for very complex relationships

---

## 8. Use Cases

* Sales analysis
* Customer insights
* Business reporting

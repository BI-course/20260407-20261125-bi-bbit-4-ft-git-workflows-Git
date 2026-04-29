# Warehouse Schema: Star Schema

## 1. Overview
A star schema is a data warehouse design model where a central fact table is connected to multiple dimension tables, forming a structure that resembles a star. It is commonly used in data warehousing to simplify complex queries and improve performance in analytical processing.


## 2. Structure of a Star Schema

The schema consists of:
- One fact table (at the center)
- Multiple dimension tables (surrounding the fact table)

### Diagram Representation
        Customer
           |
Product — Fact Table — Date
           |
         Store



## 3. Fact Table

The fact table stores quantitative data (measurable values) and foreign keys referencing dimension tables.

### Example: Sales Fact Table

| sale_id | product_id | customer_id | date_id | store_id | amount | quantity |
|--------|-----------|------------|--------|----------|--------|----------|

Characteristics:
- Contains numeric data (e.g., sales amount, quantity)
- Uses foreign keys to connect to dimension tables
- Represents business events (e.g., a sale)



## 4. Dimension Tables

Dimension tables store descriptive attributes that provide context to the data in the fact table.

### Example Dimension Tables:

#### Product Dimension
| product_id | product_name | category | price |

#### Customer Dimension
| customer_id | name | gender | location |

#### Date Dimension
| date_id | day | month | year |

#### Store Dimension
| store_id | store_name | region |

Characteristics:
- Contain descriptive, textual data
- Typically denormalized (not split into multiple related tables)
- Used for filtering, grouping, and labeling data

---

## 5. Example Scenario

In a retail sales system:
 Each record in the fact table represents a sale
The sale is linked to:
  - A product
  - A customer
  - A date
  - A store

### Sample Queries:
- Total sales per month
- Sales by region
- Best-selling products
- Customer purchase trends

---

## 6. Advantages of Star Schema

- Simple and easy to understand
- Faster query performance due to fewer joins
- Optimized for reporting and data analysis
- Widely used in Business Intelligence systems

---

## 7. Conclusion

The Star Schema is an effective data modeling technique in data warehousing. Its simple structure makes it ideal for querying large datasets and generating insights, making it a preferred choice for analytical systems.

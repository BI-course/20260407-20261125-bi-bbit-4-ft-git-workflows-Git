# Data Warehouse Schema: Retail Business

## Business Context
This data warehouse supports analytical reporting and business intelligence for a retail business. Key business processes include sales transactions, inventory management, customer analysis, and promotional effectiveness.

## Architecture Overview
- **Star Schema** with fact and dimension tables.
- **Conformed dimensions** for consistency across fact tables.
- **Slowly Changing Dimensions (SCD)** – Type 2 for Customer and Product dimensions to track history.

---

## Fact Tables

### 1. FactSales
Stores individual sales transaction lines.

| Column Name | Data Type | Description |
|-------------|-----------|-------------|
| sales_key | BIGINT | Surrogate key (PK) |
| transaction_id | VARCHAR(50) | Business transaction ID |
| product_key | BIGINT | FK to DimProduct |
| customer_key | BIGINT | FK to DimCustomer |
| store_key | BIGINT | FK to DimStore |
| date_key | INT | FK to DimDate (YYYYMMDD) |
| promotion_key | BIGINT | FK to DimPromotion |
| quantity_sold | INT | Number of units sold |
| unit_price | DECIMAL(10,2) | Price per unit at time of sale |
| discount_amount | DECIMAL(10,2) | Discount applied to line item |
| sales_amount | DECIMAL(10,2) | Calculated: (quantity * unit_price) - discount |
| cost_amount | DECIMAL(10,2) | Cost of goods sold for the line |

**Grain:** One row per product line item per sales transaction.

---

### 2. FactInventory
Daily snapshot of inventory levels.

| Column Name | Data Type | Description |
|-------------|-----------|-------------|
| inventory_key | BIGINT | Surrogate key (PK) |
| product_key | BIGINT | FK to DimProduct |
| store_key | BIGINT | FK to DimStore |
| date_key | INT | FK to DimDate |
| opening_stock | INT | Quantity at start of day |
| received_quantity | INT | Quantity received during day |
| sold_quantity | INT | Quantity sold during day |
| closing_stock | INT | Quantity at end of day |
| stock_value | DECIMAL(12,2) | closing_stock * unit_cost |

**Grain:** One row per product per store per day.

---

## Dimension Tables

### 3. DimDate
Standard time dimension.

| Column Name | Data Type | Description |
|-------------|-----------|-------------|
| date_key | INT | PK, YYYYMMDD format |
| full_date | DATE | Actual calendar date |
| year | INT | 4-digit year |
| quarter | INT | 1-4 |
| month | INT | 1-12 |
| month_name | VARCHAR(20) | January, February… |
| week_of_year | INT | 1-53 |
| day_of_month | INT | 1-31 |
| day_of_week | VARCHAR(10) | Monday, Tuesday… |
| is_weekend | BOOLEAN | TRUE/FALSE |
| is_holiday | BOOLEAN | TRUE/FALSE |

**Grain:** One row per calendar day.

---

### 4. DimProduct (SCD Type 2)
Product information including historical changes (e.g., category reassignments).

| Column Name | Data Type | Description |
|-------------|-----------|-------------|
| product_key | BIGINT | Surrogate key (PK) |
| product_id | VARCHAR(50) | Business product code (natural key) |
| product_name | VARCHAR(255) | Display name |
| brand | VARCHAR(100) | Brand name |
| category | VARCHAR(100) | Product category |
| subcategory | VARCHAR(100) | Product subcategory |
| supplier_id | VARCHAR(50) | Supplier business ID |
| unit_cost | DECIMAL(10,2) | Current or historical cost |
| unit_price | DECIMAL(10,2) | Current or historical retail price |
| valid_from | DATE | Start date of this record version |
| valid_to | DATE | End date of this record version |
| is_current | BOOLEAN | TRUE for active version |

**Grain:** One row per product per version (when attributes change).

---

### 5. DimCustomer (SCD Type 2)
Customer profile and demographics.

| Column Name | Data Type | Description |
|-------------|-----------|-------------|
| customer_key | BIGINT | Surrogate key (PK) |
| customer_id | VARCHAR(50) | Business customer ID (natural key) |
| full_name | VARCHAR(255) | Customer name |
| email | VARCHAR(255) | Email address |
| phone | VARCHAR(50) | Phone number |
| city | VARCHAR(100) | City of residence |
| state | VARCHAR(50) | State/province |
| postal_code | VARCHAR(20) | Zip/postal code |
| country | VARCHAR(100) | Country |
| loyalty_tier | VARCHAR(20) | Bronze, Silver, Gold, Platinum |
| acquisition_date | DATE | Date first purchase made |
| valid_from | DATE | Start date of this record version |
| valid_to | DATE | End date of this record version |
| is_current | BOOLEAN | TRUE for active version |

**Grain:** One row per customer per version.

---

### 6. DimStore
Physical store or online channel.

| Column Name | Data Type | Description |
|-------------|-----------|-------------|
| store_key | BIGINT | Surrogate key (PK) |
| store_id | VARCHAR(50) | Business store ID |
| store_name | VARCHAR(255) | Name of store or online channel |
| store_type | VARCHAR(50) | Physical, Online, Pop-up, etc. |
| address | VARCHAR(255) | Street address |
| city | VARCHAR(100) | City |
| state | VARCHAR(50) | State/province |
| region | VARCHAR(50) | Sales region (North, South, East, West) |
| manager_name | VARCHAR(255) | Store manager |

**Grain:** One row per store.

---

### 7. DimPromotion
Marketing and sales promotions.

| Column Name | Data Type | Description |
|-------------|-----------|-------------|
| promotion_key | BIGINT | Surrogate key (PK) |
| promotion_id | VARCHAR(50) | Business promotion ID |
| promotion_name | VARCHAR(255) | e.g., "Black Friday 2025" |
| promotion_type | VARCHAR(50) | Discount, BOGO, Free Shipping, etc. |
| discount_percent | DECIMAL(5,2) | Percentage discount if applicable |
| start_date | DATE | Promotion start date |
| end_date | DATE | Promotion end date |

**Grain:** One row per promotion.

---

## Relationships Diagram (Conceptual)

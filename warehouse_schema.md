# Star Schema Architecture in Business Intelligence

The Star Schema is the primary dimensional modeling pattern used to optimize
analytical data warehouses for high-performance read-heavy workloads.

## 1. Structural Components
### The Fact Table
- Central table containing quantitative metrics (measures) like sales or revenue.
- Stores foreign keys that link directly to surrounding dimension tables.
- Defines the "grain" or level of detail for each recorded business event.

### Dimension Tables
- Descriptive tables providing context (attributes) like Product, Time, or Store.
- Used for filtering, grouping, and labeling data in BI dashboards.
- Designed to be highly descriptive for intuitive business user access.

## 2. Core Design Principles
- **Denormalization**: Intentionally introduces redundancy to eliminate complex
  joins, ensuring the fastest possible data retrieval for large datasets.
- **Surrogate Keys**: Uses system-generated integers as primary keys to handle
  Slowly Changing Dimensions (SCD) and decouple from source system keys.
- **One-to-Many Relationships**: Each dimension table has a one-to-many
  relationship with the central fact table.

## 3. Benefits for Business Intelligence
- **Query Performance**: The simple structure allows database engines to execute
  aggregations and filters with minimal computational overhead.
- **Predictability**: BI tools like Power BI and Tableau are natively optimized
  to recognize and process star schemas as the standard data source.
- **User Accessibility**: The model mirrors business logic, making it easy for
  non-technical users to "slice and dice" data independently.

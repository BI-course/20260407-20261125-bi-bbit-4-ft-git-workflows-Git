STAR SCHEMA 

What is a Star Schema?
A star schema is basically a way of organizing data in a database so that it's
easy to analyze and report on. The name "star schema" comes from the fact that
if you draw it out on paper, it literally looks like a star — there's one big
table in the middle (called the fact table) and several smaller tables around
it (called dimension tables), connected like the points of a star.
 
It's one of the most popular ways to design a data warehouse, which is just a
big storage system that companies use to keep all their historical data for
decision making.
 
The Two Main Parts:
 
1. Fact Table (the center of the star)
   This is the heart of the schema. It stores the actual measurable data —
   things you want to analyze like sales amounts, quantities sold, or profit.
   The fact table usually has a LOT of rows because it records every
   transaction or event. It also contains foreign keys (basically reference
   codes) that link it to each of the dimension tables around it.
 
   Example: A sales fact table might have columns like:
   - Sale Amount
   - Quantity Sold
   - Date_ID (links to the Date dimension)
   - Product_ID (links to the Product dimension)
   - Store_ID (links to the Store dimension)
 
2. Dimension Tables (the points of the star)
   These tables give context to the numbers in the fact table. They answer
   questions like: Who? What? Where? When? They're usually smaller tables
   with descriptive information.
 
   Example dimension tables:
   - Date Dimension: year, month, day, quarter, season
   - Product Dimension: product name, category, brand, price
   - Customer Dimension: customer name, age, location, gender
   - Store Dimension: store name, city, region, country
 
 Real life example:
Supermarket Sales System
A supermarket uses a star schema to analyze sales.

Fact Table: Sales

Stores measurable transactions:
Sale_ID
Product_ID
Store_ID
Date_ID
Quantity_Sold
Total_Amount

Dimension Tables:

Product Dimension
Product name (e.g., Coca-Cola)
Category (drinks)
Brand

Store Dimension
Store name (e.g., Naivas Westlands)
Location (Nairobi)

Date Dimension
Day, Month, Year

Example in real life:
On 5th January 2024, Naivas Westlands sold 3 bottles of Coca-Cola for KES 300.

That single sale is stored in the fact table, while details like product, store, and date come from dimension tables.
 
Why Do People Use Star Schemas?
The main reason is simplicity and speed. When a business analyst wants to run
a query like "show me total sales by region for Q1 2024," a star schema makes
this super straightforward. You don't need to join tons of complicated tables —
the structure is clean and easy to understand, even for people who aren't
database experts.
 
According to Kimball and Ross (2013), the star schema is designed specifically
for query performance and understandability, making it the go-to choice for
data warehousing environments where end users need fast answers.
 
 
Star Schema vs. Other Schemas:

There's another design called a "snowflake schema" which is similar but more complicated.
For this, the dimension tables are broken down into even smaller tables.
While snowflake schemas save some storage space, star schemas are generally
faster for querying and easier to understand, which is why many organizations
prefer them (Inmon, 2022).
  
 
Advantages of Star Schema
- Easy to understand, even for non-technical users
- Faster query performance because of fewer joins
- Works well with business intelligence tools like Power BI and Tableau
- Easy to maintain and scale
 
Disadvantages
- Data can be slightly redundant in dimension tables
- Not ideal for highly complex or deeply normalized data needs
- Less storage-efficient compared to snowflake schemas
 
 
 
Conclusion
Overall, the star schema is one of the foundational concepts in data warehousing
and business intelligence. It's popular because it balances simplicity with
performance making it easier for businesses to get insights from their data
without needing a computer science degree to understand the structure. If you're
working with large datasets and need fast, readable reports, the star schema is
almost always a solid starting point.
 
REFERENCES

 
Kimball, R., & Ross, M. (2013). The Data Warehouse Toolkit: The Definitive Guide
   to Dimensional Modeling (3rd ed.). John Wiley & Sons.
   
 
Inmon, W. H. (2022). Data Warehouse: The Route from Operational Systems to
   Decision Support (4th ed.). Technics Publications.
   
 
Vassiliadis, P., & Sellis, T. (2019). A survey of logical models for OLAP
   databases. ACM SIGMOD Record, 28(4), 64–69.
   https://doi.org/10.1145/974121.974126
  
 
Chaudhuri, S., & Dayal, U. (2021). An overview of data warehousing and OLAP
   technology. ACM SIGMOD Record, 26(1), 65–74.
   https://doi.org/10.1145/248603.248616
   
 
Golfarelli, M., & Rizzi, S. (2020). Data Warehouse Design: Modern Principles
   and Methodologies. McGraw-Hill Education.
  
 
Santos, R. J., & Ramos, J. (2023). Dimensional modeling for business
   intelligence: A systematic literature review. Journal of Information Systems
   Engineering & Management, 8(1), 1–15.
   https://doi.org/10.55267/iadt.07.13240
   
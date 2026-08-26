# Star Schema in Data Warehousing

## What is a Star Schema?
A Star Schema is a type of database schema used in data warehousing 
that organizes data into fact and dimension tables, resembling a star shape.

## Fact Tables
A fact table stores quantitative data (measures) for analysis, such as 
sales amounts, quantities, or revenue. It sits at the center of the schema 
and contains foreign keys linking to dimension tables.

## Dimension Tables
Dimension tables store descriptive attributes related to the facts, 
such as time, location, product, or customer information. They surround 
the fact table like points of a star.

## How it is Used in Data Warehousing
Star Schemas are widely used in Business Intelligence because they:
- Simplify complex queries
- Improve query performance
- Make data easier to understand for analysts
# Data Pipelines: ETL vs ELT vs EtLT

## Overview
Data pipelines move and transform raw data from source systems 
into a format suitable for analysis. The three dominant approaches 
differ in where and when transformation occurs, which has significant 
implications for compliance with legal and regulatory requirements.

## ETL (Extract, Transform, Load)
Data is extracted from the source, transformed in a staging area 
outside the data warehouse, then loaded in a clean state.

- **Compliance advantage:** Sensitive data such as PII can be 
  masked, anonymized, or filtered before it ever enters the 
  warehouse, reducing exposure under regulations like GDPR or Kenya's 
  Data Protection Act 2019.
- **Limitation:** Slower and less flexible — transformations must 
  be defined upfront.

## ELT (Extract, Load, Transform)
Raw data is loaded directly into the warehouse first, then 
transformed inside it using tools like dbt.

- **Compliance risk:** Raw PII enters the warehouse in full, 
  requiring strict access controls and auditing within the warehouse 
  itself to meet legal obligations.
- **Advantage:** Faster ingestion and more flexible transformations 
  since all raw data is preserved.

## EtLT (Extract, transform, Load, Transform)
A hybrid approach where a lightweight transformation is applied 
before loading (e.g. deduplication or basic masking), followed 
by a second, deeper transformation inside the warehouse.

- **Compliance advantage:** Allows early anonymization of sensitive 
  fields before loading, while retaining the flexibility of 
  in-warehouse transformation for everything else.
- **Use case:** Ideal for industries with strict data residency 
  or privacy laws where raw PII must never be stored unmasked.

## Summary
The choice between ETL, ELT, and EtLT is not purely technical — 
it is a legal and governance decision. Industries handling sensitive 
personal data must carefully consider where transformation occurs 
and what data is stored at each stage.
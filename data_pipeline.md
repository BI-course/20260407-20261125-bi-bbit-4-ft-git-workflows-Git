# Data Pipelines: ETL vs ELT vs EtLT

## Introduction
Data pipelines are important in Business Intelligence because they control how data is collected, processed, and stored for analysis. The three main methods are ETL, ELT, and EtLT, each affecting performance and compliance with laws.

---

## ETL (Extract, Transform, Load)
ETL extracts data from source systems, transforms it into the right format, and then loads it into a data warehouse.

### Key Characteristics:
- Data is cleaned and transformed **before storage**
- Sensitive data gets processed early
- Good for industries with strict rules

### Compliance Perspective:
ETL works well for regulated industries (like healthcare and finance) because:
- Sensitive data (like personal information) can be anonymized before storage
- Lowers the chance of storing non-compliant raw data

---

## ELT (Extract, Load, Transform)
ELT first loads raw data into a data warehouse and then transforms it.

### Key Characteristics:
- Faster at moving large amounts of data
- Transformation happens within the data warehouse

### Compliance Perspective:
- Raw data, including sensitive information, is stored before processing
- Needs strong access controls and encryption
- Could break regulations if not managed properly

---

## EtLT (Extract, Transform, Load, Transform)
EtLT combines aspects of both ETL and ELT, where:
1. The first transformation happens before loading
2. Additional transformations are done after loading

### Key Characteristics:
- Mixes the benefits of ETL and ELT
- Flexible and can grow with needs

### Compliance Perspective:
- Some sensitive data can be treated before storage
- More compliance transformations can be done later
- Balances performance with regulatory needs

---

## Comparison Summary

| Approach | Transformation Stage | Compliance Strength | Performance |
|----------|--------------------|-------------------|------------|
| ETL      | Before loading     | High              | Moderate   |
| ELT      | After loading      | Low–Moderate      | High       |
| EtLT     | Before & After     | High              | High       |

---

## Conclusion
Choosing between ETL, ELT, and EtLT depends on the need for performance versus regulatory compliance. ETL is safest for industries with strict rules, ELT is best for speed and scalability, while EtLT provides a flexible approach for modern data systems that need both efficiency and compliance.

---

## Related Issue
Closes #4

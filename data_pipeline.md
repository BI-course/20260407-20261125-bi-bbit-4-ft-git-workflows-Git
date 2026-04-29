# Data Pipeline Approaches: ETL, ELT, and EtLT

## Overview

Modern data pipelines move data from source systems into a destination
such as a data warehouse or data lake. Three dominant approaches exist:
Extract, Transform, Load (ETL); Extract, Load, Transform (ELT); and
Extract, transform, Load, Transform (EtLT). The choice between them has
significant implications for regulatory compliance and data governance,
particularly in industries subject to strict legal requirements such as
healthcare, finance, and telecommunications.

---

## 1. ETL (Extract, Transform, Load)

Data is extracted from source systems, transformed in a staging area
outside the destination, and only the cleaned/masked result is loaded
into the warehouse.

**Compliance strengths:**
- Sensitive data (e.g., PII, PHI) can be masked or anonymised
  *before* it ever reaches the warehouse, reducing the attack surface.
- Easier to demonstrate to auditors that raw personal data was never
  stored in the analytical environment.
- Well-suited for regulations such as Kenya's Data Protection Act 2019,
  the EU GDPR, and HIPAA, which require data minimisation.

**Limitations:**
- Transformation logic lives outside the warehouse, making it harder
  to audit end-to-end lineage from a single location.
- Slower to adapt when compliance rules change, since pipelines must
  be rebuilt before data reaches analysts.

---

## 2. ELT (Extract, Load, Transform)

Raw data is loaded into the destination first; transformations happen
inside the warehouse using its own compute engine.

**Compliance strengths:**
- Full raw data is preserved, providing a complete audit trail —
  useful when regulators require proof of original records.
- Transformation logic is version-controlled inside the warehouse
  (e.g., dbt models), making compliance audits more straightforward.

**Limitations:**
- Raw data, including PII, sits in the warehouse until transformed.
  This increases the risk of unauthorised exposure and may conflict
  with data minimisation principles under GDPR or the DPA 2019.
- Requires robust role-based access controls (RBAC) to restrict who
  can query raw tables before transformation is complete.

---

## 3. EtLT (Extract, transform, Load, Transform)

A hybrid approach: a lightweight transformation is applied during
extraction (e.g., hashing PII fields), the partially cleaned data is
loaded, and a second, heavier transformation runs inside the warehouse.

**Compliance strengths:**
- The initial transform step can strip or hash regulated fields
  (e.g., national ID numbers, phone numbers) before they leave the
  source environment, satisfying data minimisation requirements.
- The second transform step inside the warehouse handles business
  logic, with full lineage tracking.
- Balances the audit trail benefits of ELT with the privacy
  protections of ETL, making it well-suited for industries like
  telecommunications and financial services operating under
  overlapping regulatory frameworks.

**Limitations:**
- Two separate transformation layers increase architectural complexity
  and the number of points where compliance logic can drift or fail.
- Requires clear documentation of what each layer transforms to
  avoid confusion during regulatory audits.


## Conclusion

No single approach is universally compliant. The right choice depends
on the regulatory environment, the sensitivity of the data being
processed, and the organisation's capacity to implement access controls.
EtLT is increasingly preferred in regulated industries because it
applies privacy protections early in the pipeline while retaining the
flexibility and auditability of warehouse-native transformations.
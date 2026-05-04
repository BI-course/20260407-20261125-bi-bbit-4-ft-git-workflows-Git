1. **ETL — Extract, Transform, Load**

Data is cleaned and transformed before it enters the destination (typically a data warehouse).

***Compliance implications:***

a)Data minimization: Sensitive fields (PII, PHI) can be masked, anonymized, or dropped before they ever land in the warehouse 

b)Audit trail risk: Because raw data never reaches the destination, it can be harder to prove the original state of records during a regulatory audit. You need to preserve raw source logs separately.

c) Access control simplicity: Fewer systems store sensitive data, reducing your compliance surface area.

d)Reduced exposure risk- Since raw data isn’t stored in the warehouse, there’s less chance of accidental access to sensitive information.

e)Easier data minimization-You only load what you actually need, which aligns well with legal principles like “data minimization.”

Downside: Transformation logic lives in middleware (e.g., custom scripts), which can be opaque and harder to audit than SQL-based transformations.



2. **ELT — Extract, Load, Transform**
Raw data lands in the destination first, transformations happen inside the warehouse (e.g., BigQuery, Snowflake, dbt).

**Compliance implications:**

a)Full raw data retention: The warehouse holds raw, untransformed data — great for audit completeness, but means your warehouse now stores sensitive/regulated data and must meet the same compliance standards as source systems.

b)Transformation auditability: Since transforms are SQL/dbt models, they're version-controlled and inspectable — strong audit trail for how derived metrics were computed.

c)Data residency risk: If your cloud warehouse is in a foreign jurisdiction, loading raw data there may violate data residency requirements (e.g., EU data staying in the EU, or Kenya's DPA requiring local storage of certain citizen data).

d)Role-based access becomes critical: Raw tables must be locked down tightly with column-level security or dynamic data masking.



3. **EtLT — Extract, (light) transform, Load, Transform**
A hybrid: a lightweight transformation happens before loading (e.g., PII masking, deduplication, format normalization), then full analytical transformation happens in the warehouse.

**Compliance implications:**

a)Best of both: Sensitive fields are anonymized or tokenized before they touch the warehouse (ETL benefit), while the analytical transformation logic remains transparent and auditable in the warehouse (ELT benefit).

b)Tokenization workflows: A common EtLT pattern for compliance — replace a national ID or phone number with a token before loading; maintain the token-to-identity mapping in a separate, tightly controlled vault.

c)Complexity overhead: Two transformation layers mean two points of audit — you must document both the pre-load logic and the in-warehouse logic for a regulator.


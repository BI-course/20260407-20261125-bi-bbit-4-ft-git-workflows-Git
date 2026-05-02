
# Data Pipeline Architectures: ETL, ELT, and EtLT

## 1. ETL (Extract, Transform, Load)

ETL is the traditional pipeline architecture where data is extracted
from source systems, transformed in a staging environment, and then
loaded into a target data warehouse.

**Process:**
1. **Extract** – Raw data is pulled from sources (databases, APIs, flat files)
2. **Transform** – Data is cleaned, validated, and restructured *before* it enters the warehouse
3. **Load** – Only the processed, compliant data enters the warehouse

**Compliance advantage:** Because sensitive data is transformed
before loading, personally identifiable information (PII) can be
masked, anonymised, or dropped before it ever touches the warehouse.
This aligns well with regulations like GDPR (EU) and HIPAA (US
healthcare), which enforce data minimisation — only storing what is
strictly necessary.

**Limitation:** Transformations are rigid. If business requirements
change, raw data may already be discarded and unrecoverable.



## 2. ELT (Extract, Load, Transform)

ELT reverses the transformation step. Raw data is loaded directly
into the warehouse first, and transformations happen inside the
warehouse using its own compute power (e.g., BigQuery, Snowflake).

**Process:**
1. **Extract** – Raw data is pulled from source systems
2. **Load** – Raw data is loaded *as-is* into the warehouse
3. **Transform** – Data is transformed inside the warehouse on demand

**Compliance risk:** Raw data — including unmasked PII — lands in the
warehouse before any filtering occurs. This can violate GDPR's data
minimisation principle and HIPAA's minimum necessary standard if
access controls are not extremely strict. Organisations using ELT
must implement robust role-based access control (RBAC) and audit
logging to remain compliant.

**Advantage:** Full raw data is preserved, giving analysts
flexibility to re-transform data as requirements evolve.



## 3. EtLT (Extract, transform, Load, Transform)

EtLT is a hybrid approach that combines the compliance strengths of
ETL with the flexibility of ELT. A lightweight transformation occurs
before loading (e.g., masking PII, filtering illegal fields), and a
second, more complex transformation occurs inside the warehouse.

**Process:**
1. **Extract** –  The Raw data is pulled from source systems . mm
2. **transform** – A minimal transformation strips or masks sensitive
   fields (lowercase "t" = lightweight, not full restructuring)
3. **Load** – Partially cleaned data enters the warehouse
4. **Transform** – Full business logic transformations run inside the warehouse

**Compliance advantage:** PII and legally restricted fields are
removed or pseudonymised before they enter the warehouse, satisfying
data minimisation requirements. The warehouse still receives rich
data for flexible analytics.

**Use case example:** A healthcare analytics platform extracting
patient records would use EtLT to strip direct identifiers (name,
ID number) before loading, while retaining clinical data for
transformation and analysis inside the warehouse.



## Compliance Summary Table

| Architecture | PII enters warehouse? | Flexibility | Regulatory fit |
|---|---|---|---|
| ETL | No (stripped before load) | Low | Strong (GDPR, HIPAA) |
| ELT | Yes (raw data loaded) | High | Risky without strict RBAC |
| EtLT | Partial (masked before load) | High | Strong + flexible |



## Key Regulations Referenced

- **GDPR (General Data Protection Regulation)** – EU law requiring
  data minimisation, purpose limitation, and the right to erasure.
- **HIPAA (Health Insurance Portability and Accountability Act)** –
  US law requiring minimum necessary access to protected health
  information (PHI).
- **POPIA (Protection of Personal Information Act)** – South African
  equivalent of GDPR, relevant for organisations operating locally.




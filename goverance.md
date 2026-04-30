# Data Governance and PII Access Control

## What is Data Governance?

Data governance is the framework of policies, procedures, and standards that ensure data is managed properly throughout its lifecycle. It encompasses data quality, security, privacy, and compliance.

In a Business Intelligence context, governance determines:

- **Who** can access what data
- **When** and **how** data can be used
- **What** security controls must be in place
- **How** compliance with regulations is demonstrated

## Personally Identifiable Information (PII)

### Definition

PII refers to any information that can be used to distinguish or trace an individual's identity, either directly or indirectly when combined with other data.

### Categories of PII

| Category                 | Examples                                                                   | Risk Level |
| ------------------------ | -------------------------------------------------------------------------- | ---------- |
| **Sensitive PII**        | Social Security numbers, passport numbers, biometric data, medical records | Critical   |
| **Direct Identifiers**   | Full name, email address, phone number, physical address, government ID    | High       |
| **Indirect Identifiers** | Date of birth, ZIP code, gender, IP address, device ID                     | Medium     |

## Access Control Principles for PII

### 1. Least Privilege Principle

Users should only have access to the minimum data necessary for their job function. A marketing analyst may need customer email addresses but not Social Security numbers.

### 2. Role-Based Access Control (RBAC)

| Role                   | Access Level                                          |
| ---------------------- | ----------------------------------------------------- |
| **Data Steward**       | Full access + governance rights + audit capabilities  |
| **BI Analyst**         | Read access to anonymized datasets + aggregated views |
| **Compliance Officer** | Audit logs + metadata only + schema access            |
| **External Vendor**    | No PII access, only aggregated reports                |

### 3. Data Minimization

Only collect and retain PII that is strictly necessary. In BI pipelines, this means:

- Anonymizing data at the extraction stage when possible
- Implementing data masking in development environments
- Purging PII after retention periods expire
- Using aggregation instead of row-level access

## Compliance Requirements by Industry

| Industry             | Regulation    | Key PII Requirements                                                                                            |
| -------------------- | ------------- | --------------------------------------------------------------------------------------------------------------- |
| Healthcare           | HIPAA         | Protected Health Information (PHI) requires encryption at rest and in transit, access logs retained for 6 years |
| Finance              | GLBA, PCI-DSS | Customer financial data must be tracked, audited quarterly                                                      |
| EU Citizens          | GDPR          | Right to access, right to be forgotten, breach notification within 72 hours                                     |
| California Residents | CCPA          | Opt-out rights, data portability, disclosure requirements                                                       |

## Best Practices for PII in Data Pipelines

### Before Extraction (Planning Phase)

- [ ] Conduct a data inventory (what PII exists and where?)
- [ ] Classify data by sensitivity level
- [ ] Document legal basis for processing
- [ ] Assign a data owner for each PII dataset

### During Transformation (ETL/ELT Phase)

Example: Masking PII in a SQL view for analysts

\`\`\`sql
-- Create a secured view that masks PII for non-privileged users
CREATE VIEW customer\*analytics_secured AS
SELECT
customer_id,
LEFT(email, 2) + '\*\**' + RIGHT(email, 5) as masked*email,
LEFT(phone, 3) + '\*\*\*-\*\*\*\*' as masked_phone,
city_region as geography,
age_range,
purchase_history
FROM raw_customer_data
WHERE access_level IN ('ANALYST_VIEW', 'BI_USER');
\`\`\`

## References for Further Reading

- NIST Special Publication 800-122 - Guide to Protecting PII
- GDPR Article 4(1) - Definition of personal data
- ISO/IEC 27001:2022 - Information security management

_Created for Business Intelligence Lab - Collaborative Git Workflows (2026)_
_100% Complete Milestone - Issue #5_
EOF

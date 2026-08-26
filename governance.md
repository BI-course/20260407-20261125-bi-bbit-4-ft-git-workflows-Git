# Data Governance and Access to PII

## Overview
Data governance refers to the policies, standards, and processes 
that ensure data is accurate, consistent, secure, and used 
responsibly across an organization. It is the foundation upon 
which trustworthy BI systems are built.

## Key Components of Data Governance

### 1. Data Ownership
Every dataset must have a clearly assigned owner — a person or 
team accountable for its accuracy, accessibility, and compliance. 
Without ownership, data quality degrades and accountability gaps emerge.

### 2. Data Cataloguing
A data catalog documents what data exists, where it lives, who 
owns it, and how it may be used. It enables analysts to discover 
and understand datasets without needing to ask the data team directly.

### 3. Access Control
Role-based access control (RBAC) ensures that only authorized 
personnel can view or modify sensitive data. Access should follow 
the principle of least privilege — users get only the access they 
need to do their job.

### 4. Audit Trails
All access to sensitive data should be logged. Audit trails provide 
accountability and are often a legal requirement under data 
protection regulations.

## Personally Identifiable Information (PII)

PII refers to any data that can be used to identify a specific 
individual. Examples include:
- Full name
- National ID or passport number
- Email address or phone number
- Biometric data

### Legal Framework
Under Kenya's **Data Protection Act 2019**, organizations are 
required to:
- Collect only the minimum PII necessary (data minimization)
- Store PII securely and for no longer than necessary
- Obtain informed consent before collecting personal data
- Report data breaches within 72 hours

### PII in BI Systems
BI systems often aggregate data from sources that contain PII. 
Best practices include:
- **Anonymization** — permanently removing identifying information
- **Pseudonymization** — replacing PII with tokens that can be 
  reversed only with a separate key
- **Masking** — obscuring PII in non-production environments

## Summary
Effective data governance ensures that BI systems are not only 
analytically powerful but also legally compliant and ethically 
sound. Ungoverned access to PII is both a legal liability and 
a breach of individual rights.
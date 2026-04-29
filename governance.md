# Data Governance and PII Management Framework

## 1. Introduction to Data Governance
Data Governance is a collection of processes, roles, policies, and standards that ensure the effective and efficient use of information in enabling an organization to achieve its goals. In the context of Business Intelligence (BI), governance ensures that the data being analyzed is accurate, consistent, and secure.

## 2. Data Stewardship and Quality
To maintain high-quality BI outputs, the following pillars are established:
* **Accuracy:** Ensuring data reflects the real-world objects or events it represents.
* **Consistency:** Maintaining uniform data definitions across different departments (e.g., ensuring "Revenue" is calculated the same way by Finance and Sales).
* **Traceability:** Keeping a record of the data's lineage—from its source system through the ETL (Extract, Transform, Load) process to the final report.

## 3. Personally Identifiable Information (PII)
PII refers to any information that can be used to distinguish or trace an individual‘s identity. Under the **Kenya Data Protection Act (2019)**, protecting this data is a legal mandate.

### Examples of PII in BI Systems:
* **Direct Identifiers:** Full names, National ID numbers, Passport numbers, and Phone numbers.
* **Indirect Identifiers:** Home addresses, IP addresses, and biometric data.

## 4. Access Control and Security Protocols
To protect sensitive data while still allowing for meaningful business analysis, the following protocols are implemented:

| Protocol | Description |
| :--- | :--- |
| **RBAC** | **Role-Based Access Control:** Users are granted access based on their job function (e.g., a Marketing Analyst sees trends, but not customer ID numbers). |
| **Data Masking** | Obscuring specific data elements (e.g., showing only the last four digits of a phone number) within the BI tool. |
| **Anonymization** | The process of removing PII from a dataset so that the remaining data cannot be linked back to an individual. |
| **Encryption** | Ensuring data is unreadable to unauthorized users both "at rest" (stored in the database) and "in transit" (moving across the network). |

## 5. Audit and Compliance
Data governance requires a clear audit trail. Every access request, data modification, and report generation involving PII must be logged. This ensures accountability and provides the necessary documentation for industrial assessors or regulatory bodies during an audit.
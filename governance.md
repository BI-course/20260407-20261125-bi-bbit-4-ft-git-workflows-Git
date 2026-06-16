# Data Governance and Access to PII

## 1. What is Data Governance?

Data governance is the framework of policies, processes, standards, and roles that organizations use to manage their data assets effectively, securely, and responsibly. It defines **who** can take **what actions** with **which data**, **under what circumstances**, and **using what methods**.

At its core, data governance ensures that data is:

- **Accurate** — trustworthy and free from errors
- **Consistent** — uniform across different systems and departments
- **Secure** — protected from unauthorized access or misuse
- **Compliant** — aligned with legal and regulatory requirements
- **Available** — accessible to those who need it, when they need it
  Data governance is not a one-time project — it is an ongoing organizational discipline that evolves alongside business needs and regulatory changes.

---

## 2. Key Components of Data Governance

### 2.1 Data Policies

Formal rules that define how data should be collected, stored, used, shared, and deleted. Policies set the standards that all employees and systems must follow.

### 2.2 Data Standards

Agreed-upon formats, definitions, and naming conventions that ensure consistency across the organization. For example, standardizing date formats (YYYY-MM-DD) or customer ID structures.

### 2.3 Data Roles and Responsibilities

Clear ownership and accountability are central to governance. Common roles include:

| Role                              | Responsibility                                                       |
| --------------------------------- | -------------------------------------------------------------------- |
| **Data Owner**                    | Senior stakeholder accountable for a data domain (e.g. Finance data) |
| **Data Steward**                  | Day-to-day manager of data quality and policy compliance             |
| **Data Custodian**                | IT/technical team responsible for storage and security               |
| **Data Consumer**                 | Any employee or system that uses the data                            |
| **Data Protection Officer (DPO)** | Ensures compliance with data protection laws (required under GDPR)   |

### 2.4 Data Lifecycle Management

Governance covers data from creation to deletion — including collection, storage, processing, sharing, archiving, and disposal. Each stage has specific rules and controls.

### 2.5 Data Quality Management

Processes to measure, monitor, and improve data quality across dimensions such as completeness, accuracy, consistency, timeliness, and validity.

### 2.6 Metadata Management

Managing data about data — descriptions, definitions, lineage, and classifications — so that users understand what data exists, where it came from, and how it should be used.

---

## 3. Data Governance Frameworks

Several established frameworks guide organizations in implementing data governance:

### 3.1 DAMA-DMBOK (Data Management Body of Knowledge)

The most widely recognized framework in data management. It defines 11 knowledge areas including Data Governance, Data Architecture, Data Quality, and Data Security. It provides a comprehensive guide for organizations building governance programs.

### 3.2 COBIT (Control Objectives for Information and Related Technologies)

A framework developed by ISACA focused on IT governance and management. It helps organizations align IT processes — including data management — with business goals and regulatory requirements.

### 3.3 GDPR Compliance Framework

The General Data Protection Regulation (EU, 2018) essentially functions as a governance framework for personal data, mandating documentation, accountability, and technical safeguards.

### 3.4 The Data Governance Institute (DGI) Framework

Provides a practical model for establishing governance programs, covering rules of engagement, decision rights, and accountabilities across people, processes, and technology.

---

## 4. What is PII?

**Personally Identifiable Information (PII)** refers to any data that can be used — on its own or in combination with other data — to identify, contact, or locate a specific individual.

Examples of PII include:

- Full name
- National ID or passport number
- Email address
- Phone number
- Physical address
- Date of birth
- Biometric data (fingerprints, facial recognition)
- IP address
- Medical records
- Financial account numbers
- GPS/location data
  PII is considered sensitive because its exposure can lead to identity theft, financial fraud, discrimination, or personal harm. Organizations that collect, store, or process PII have a legal and ethical obligation to protect it.

---

## 5. Types of PII

PII is generally categorized into two types:

### 5.1 Direct Identifiers

Information that can identify an individual on its own, without needing additional data.

Examples: Full name, national ID number, passport number, biometric data, email address.

### 5.2 Indirect Identifiers (Quasi-Identifiers)

Information that does not directly identify an individual but can do so when combined with other data points.

Examples: Gender, date of birth, postcode, employer, job title.

> **Example:** Knowing someone's gender, age, and postcode may not identify them individually, but combining all three can often narrow it down to a single person.

### 5.3 Sensitive PII

A subset of PII that carries a higher risk of harm if disclosed. This includes:

- Health and medical information
- Race or ethnic origin
- Religious beliefs
- Sexual orientation
- Financial information
- Criminal records
- Children's data
  Sensitive PII typically requires stronger legal justification to process and stricter access controls.

---

## 6. Legal Frameworks Governing PII

### 6.1 GDPR — General Data Protection Regulation (European Union, 2018)

One of the world's strictest data protection laws. Key principles include:

- **Lawfulness, fairness, and transparency** — data must be processed legally and openly
- **Purpose limitation** — data collected for one purpose cannot be reused for another
- **Data minimisation** — only collect what is strictly necessary
- **Accuracy** — data must be kept up to date
- **Storage limitation** — data must not be kept longer than necessary
- **Integrity and confidentiality** — data must be protected from unauthorized access
- **Accountability** — organizations must be able to demonstrate compliance
  Penalties for non-compliance can reach up to €20 million or 4% of global annual turnover.

### 6.2 Kenya Data Protection Act (2019)

Kenya's primary data protection legislation, modelled in part on the GDPR. It:

- Establishes the Office of the Data Protection Commissioner (ODPC)
- Requires registration of data controllers and processors
- Gives individuals rights over their data (access, correction, deletion)
- Regulates the transfer of personal data outside Kenya
- Applies to any organization processing data of Kenyan residents

### 6.3 HIPAA — Health Insurance Portability and Accountability Act (USA, 1996)

Governs the protection of health-related PII (Protected Health Information / PHI) in the healthcare industry. Requires strict access controls, audit trails, and breach notification procedures.

### 6.4 CCPA — California Consumer Privacy Act (USA, 2020)

Gives California residents rights over their personal data including the right to know, delete, and opt out of the sale of their data.

---

## 7. Controlling Access to PII

Controlling who can access PII is one of the most critical aspects of data governance. The following controls are commonly applied:

### 7.1 Role-Based Access Control (RBAC)

Access to PII is granted based on an individual's role in the organization. Employees can only access the data they need to perform their job function. For example, a marketing analyst should not have access to medical records.

### 7.2 Principle of Least Privilege

Every user and system should have the **minimum level of access** required to perform their function — nothing more. This limits the potential damage caused by insider threats or compromised accounts.

### 7.3 Data Masking

Sensitive fields in a dataset are obscured or replaced with fictional values when displayed to unauthorized users. For example, a customer service agent may see `****-****-****-1234` instead of a full credit card number.

### 7.4 Anonymisation

The process of irreversibly removing all identifying information from a dataset so that individuals can no longer be identified. Truly anonymised data falls outside the scope of most data protection laws.

### 7.5 Pseudonymisation

Replacing identifying fields with artificial identifiers (pseudonyms). Unlike anonymisation, the original data can be restored with access to a separate key. Pseudonymised data is still considered PII under GDPR.

### 7.6 Encryption

PII should be encrypted both **at rest** (when stored) and **in transit** (when transmitted). Encryption ensures that even if data is intercepted, it cannot be read without the decryption key.

### 7.7 Audit Trails and Access Logs

All access to PII should be logged — recording who accessed what data, when, and why. Audit trails are essential for detecting unauthorized access and demonstrating compliance during regulatory audits.

### 7.8 Multi-Factor Authentication (MFA)

Requiring more than one form of verification before granting access to systems containing PII adds an additional layer of protection against unauthorized access.

---

## 8. Data Breaches and PII

A **data breach** occurs when PII is accessed, disclosed, altered, or destroyed without authorization. Breaches can result from:

- Cyberattacks (hacking, phishing, ransomware)
- Insider threats (employee misuse)
- Human error (sending data to the wrong recipient)
- System vulnerabilities

### 8.1 Consequences of a Data Breach

- **Legal penalties** — heavy fines under GDPR, CCPA, or the Kenya Data Protection Act
- **Reputational damage** — loss of customer trust
- **Financial loss** — cost of remediation, legal fees, compensation
- **Harm to individuals** — identity theft, fraud, discrimination

### 8.2 Breach Notification Requirements

Under most data protection laws, organizations must notify:

- The **relevant regulatory authority** (e.g. ODPC in Kenya, ICO in the UK) within 72 hours of becoming aware of a breach (GDPR standard)
- **Affected individuals** if the breach poses a high risk to their rights and freedoms

---

## 9. Best Practices for Data Governance and PII Protection

| Best Practice               | Description                                                                                                |
| --------------------------- | ---------------------------------------------------------------------------------------------------------- |
| **Data Classification**     | Label data by sensitivity level (Public, Internal, Confidential, Restricted) to apply appropriate controls |
| **Privacy by Design**       | Build data protection into systems and processes from the start, not as an afterthought                    |
| **Regular Audits**          | Periodically review who has access to PII and whether it is still necessary                                |
| **Staff Training**          | Educate all employees on data governance policies and PII handling responsibilities                        |
| **Data Retention Policies** | Define how long PII is kept and ensure timely, secure deletion when no longer needed                       |
| **Consent Management**      | Obtain and document explicit consent before collecting PII, and allow individuals to withdraw consent      |
| **Incident Response Plan**  | Have a documented plan for responding to data breaches, including notification procedures                  |
| **Vendor Management**       | Ensure third-party vendors who process PII on your behalf also comply with governance standards            |

---

## 10. References

- DAMA International. (2017). _DAMA-DMBOK: Data Management Body of Knowledge_ (2nd ed.).
- European Parliament. (2016). _General Data Protection Regulation (GDPR) — Regulation (EU) 2016/679_.
- Government of Kenya. (2019). _The Data Protection Act, No. 24 of 2019_. Kenya Gazette Supplement.
- ISACA. (2019). _COBIT 2019 Framework: Introduction and Methodology_.
- U.S. Department of Health & Human Services. (1996). _Health Insurance Portability and Accountability Act (HIPAA)_.
- California State Legislature. (2018). _California Consumer Privacy Act (CCPA) — AB-375_.
- National Institute of Standards and Technology (NIST). (2010). _Guide to Protecting the Confidentiality of Personally Identifiable Information (PII)_ — Special Publication 800-122.

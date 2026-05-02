# Data Governance and PII Access Policy

## 1. Overview
This document outlines the foundational data governance policies for Lab 1, specifically focusing on the management, security, and access controls regarding Personally Identifiable Information (PII). The goal of these guidelines is to ensure data integrity, protect user privacy, and maintain compliance with standard regulatory frameworks.

## 2. Defining PII
Personally Identifiable Information (PII) refers to any data that can be used to distinguish or trace an individual's identity, either alone or when combined with other personal or identifying information. 

**Examples of PII include, but are not limited to:**
* Full names
* Email addresses
* Physical addresses
* Phone numbers
* Identification numbers (e.g., SSN, Passport, Driver's License)
* Biometric data
* IP addresses (in certain regulatory contexts)

## 3. Core Data Governance Principles
All team members must adhere to the following principles when handling data:

* **Data Minimization:** Only collect and retain PII that is strictly necessary for the specific task or research objective.
* **Purpose Limitation:** PII must only be used for the purpose it was originally collected. Any secondary use requires explicit re-authorization.
* **Accuracy:** Data must be kept accurate and up to date. Inaccurate data should be corrected or deleted promptly.
* **Transparency:** Data collection and processing methods must be documented and transparent to stakeholders involved.

## 4. Access to PII
Access to PII is strictly controlled to prevent unauthorized viewing, modification, or exfiltration.

### Role-Based Access Control (RBAC)
Access to systems containing PII is granted based on the Principle of Least Privilege (PoLP). Team members will only receive the minimum level of access necessary to perform their assigned duties.

* **Administrators:** Full access to manage user permissions and system configurations.
* **Researchers/Analysts:** Read-only access to specific, anonymized, or pseudonymized datasets required for analysis. Direct access to raw PII requires special authorization.
* **General Members:** No default access to PII.

### Access Logging
All access to databases or files containing PII must be logged. Logs will record:
* The identity of the user accessing the data.
* The timestamp of the access.
* The specific data accessed or queried.
* The action performed (Read, Write, Update, Delete).

## 5. Handling and Storage Requirements
* **Encryption:** All PII must be encrypted both **at rest** and **in transit**.
* **Anonymization & Pseudonymization:** Before data is used for general lab research or testing, PII must be scrubbed, masked, or pseudonymized to protect identities.
* **Secure Storage:** PII must not be stored on local, unencrypted hard drives or personal devices. All data must be stored in approved, secure cloud or physical environments.

## 6. Incident Response and Reporting
Any suspected unauthorized access, data exposure, or breach involving PII must be reported immediately to the project lead or designated security officer. Do not attempt to investigate or remediate the breach independently before reporting.
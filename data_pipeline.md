# Differences between ETL, ELT, and EtLT 
This is a document explaining the differences between ETL, ELT and EtLT in the context of compliance with the legal requirements in an industry.
## ETL (Extract, Transform, Load)
In this approach of data pipelining, the data is extracted, transformed and cleaned separately before it is loaded into  the data warehouse and it is best suitable for industries needing strict pre-data sanitization such as healthcare and finance which are governed by Health Insurance Portability and Accountability Act (HIPAA) and General Data Protection Regulation (GDPR) respectively. 
### Advantage
It ensures highest data security because sensitive data (Personal Identifiable Information) is masked before long-term storage.
### Disadvantage
It is rigid because it is difficult to re-process data if business rules change.

## ELT (Extract, Load, Transform)
Here, the data is loaded directly into the cloud data warehouse and transformation occurs within the warehouse. Since the data is loaded raw, there is need for strict security in the warehouse such as encryption and strict access controls to prevent unauthorized exposure.
### Advantage 
It preserves raw data which is valuable for audits.
### Disadvantage
There is risk exposure of the data since it is loaded in the warehouse in its raw form.

## EtLT (Extract, Transform-light, Load, Transform)
This is a hybrid approach whereby the data undergoes light transformation before it is loaded in the warehouse then goes through heavy transformation inside the data warehouse hence ensuring compliance and also providing an opportunity for cloud scalability for processing.
### Advantage
It prevents data swamps by ensuring the data warehouse does not have unmasked sensitive data.
### Disadvantage
There is risk of inconsistency due to two different transformation stages.

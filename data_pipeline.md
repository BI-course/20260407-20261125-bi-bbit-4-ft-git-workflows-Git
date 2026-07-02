# Data Pipeline
This file compares ETL, ELT, and EtLT approaches.
### Core Difference:
1. ETL: Data is transformed before it is stored.
2. ELT: Data is stored before it is transformed.
3. EtLT: Data is lightly transformed before loading, then fully transformed after loading.
### Processing Order Difference
1. ETL:	Extract → Transform → Load
2. ELT: Extract → Load → Transform
3. EtLT: Extract → Light Transform → Load → Transform
### Data Exposure Difference
1. ETL → The raw data is not stored therefore there is low exposure risk since the data is cleaned before storage.
2. ELT → The raw data is stored therefore there is a high exposure risk  since the raw data is stored before it is cleaned
3. EtLT → The raw data is partially stored therefore there is a medium exposure risk since only some of the raw data is filtered before storage.
### Transformation Location Difference
1. ETL → External processing layer (before warehouse)
2. ELT → Inside data warehouse/lake
3. EtLT → Split: light transform before load, full transform after load
### Compliance Control Point Difference
1. ETL → During transformation stage (pre-storage enforcement)
2. ELT → After data is loaded (requires strong access control)
3. EtLT → At two stages: pre-load filtering + post-load governance
### Regulatory Risk Comparison
1. ETL: it has the lowest regulatory risk since data is never stored in raw sensitive form
2. ELT: it has the highest regulatory risk since raw data is stored before controls are applied
3. EtLT: it has moderate regulatory risk since there is partial pre-control done before storage
### Compliance Suitability Difference
1. ETL → Strict compliance environments (e.g., HIPAA, PCI-DSS)
2. ELT → Less restrictive environments with strong governance tooling
3. EtLT → Mixed or evolving regulatory environments
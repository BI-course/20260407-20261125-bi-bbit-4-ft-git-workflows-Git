# Data Profiling & Source Cleaning Rules

## Overview
Based on the data sources identified in `data_source.md`, this document defines the quality checks required during the initial extraction phase to prevent "Garbage In, Garbage Out."

## 1. Transactional Databases (SQL)
- **Check:** Ensure no duplicate "Transaction_IDs" exist.
- **Rule:** Flag any record where the "Transaction_Date" is in the future.

## 2. Flat Files (CSV/Excel)
- **Check:** Verify that all numeric columns (like Price) do not contain text.
- **Rule:** Check for "Trailing Spaces" in text fields (e.g., "Nairobi " vs "Nairobi") and trim them to ensure consistency.

## 3. APIs (JSON/XML)
- **Check:** Validate the schema of the JSON response.
- **Rule:** If the API returns a "404" or "500" error code, the quality log must record a "Missing Data" event.

## 4. Streaming Data (IoT/Logs)
- **Check:** Check for "Data Latency."
- **Rule:** If the time difference between the event and the arrival is > 5 minutes, mark the data as "Stale."

## Conclusion
Profiling these sources early allows Member 2 to trust the datasets used for analysis.

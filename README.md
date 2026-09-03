# 🐝 Bee Haven: Azure Data Lakehouse & ELT Pipeline

An end-to-end cloud data engineering project built on **Microsoft Azure**, designed to ingest, structure, and transform multi-channel agricultural data and sensor telemetry for the University of Honighausen's beehive research initiative near Würzburg.

---

### 🚀 Project Overview
**Bee Haven** consolidates historical archives with ongoing batch sensor telemetry (tracking hive temperature, humidity, weight, and flow rates) alongside environmental data fetched via external APIs. To manage this influx of data efficiently, the system implements a robust **ELT (Extract, Load, Transform)** workflow anchored in the **Medallion Lakehouse Architecture**.

---

### 🛠️ Technical Stack & Azure Services
* **Cloud Platform:** Microsoft Azure
* **Storage & Data Lake:** Azure Data Lake Storage Gen2 (ADLS Gen2) with Hierarchical Namespace
* **Orchestration & Ingestion:** Azure Data Factory (ADF) utilizing dynamic content, parameters, `Get Metadata`, `ForEach` loops, and time-based triggers
* **Transformation Engine:** Azure Synapse Analytics Notebooks (Python / Pandas)
* **API Integration:** BrightSky Weather API for environmental enrichment
* **File Formats:** Raw CSV / JSON (Bronze) to Columnar Parquet (Silver/Gold layers)
* **Version Control:** Git / GitHub

---
  
### 📐 Medallion Lakehouse Architecture
The data lake is structured into three progressive refinement layers to ensure data integrity, lineage, and high-performance querying:

* **🥉 Bronze Layer (`bronze/` - Raw Landing Zone):** Stores untouched, raw CSV sensor logs and JSON API weather responses ingested directly via Azure Data Factory.
* **🥈 Silver Layer (`silver/` - Cleansed Layer):** Houses standardized, cleaned datasets where column names are normalized, missing values are handled, duplicate timestamps are clarified (departure vs. arrival flow), and data is stored as high-performance **Parquet** files alongside a unified weather table.
* **🥇 Gold Layer (`gold/` - Analytics-Ready Layer):** Contains fully aggregated and structured datasets optimised for business intelligence, reporting, and uncovering correlations between climate factors and bee health.

---

### ⚙️ Pipeline & Automation Features
* **Automated Ingestion:** Bulk-copies batch datasets from source storage into the Data Lake using ADF.
* **Dynamic Content Management:** Configures paths, archives, and custom timestamped naming conventions dynamically within pipeline loops.
* **API Integration:** Fetches historical weather observations matching the date ranges of hive telemetry to enrich environmental insights.
* **Orchestrated Scheduling:** Chains the bronze-to-silver and silver-to-gold workflows into a unified `daily-processing` pipeline running automatically via time-based triggers.

---
### 💡 Conclusion
Building the Bee Haven data pipeline demonstrates how raw, multi-channel agricultural inputs and external weather telemetry can be systematically transformed into valuable analytical assets using modern cloud architecture. By implementing an ELT approach through the Medallion Lakehouse pattern (Bronze, Silver, and Gold layers), the project successfully establishes clear data lineage, high compression efficiency via Parquet storage, and robust scalability. Furthermore, leveraging Azure Data Factory for automated, dynamic orchestration—combined with Python-driven data cleaning in Synapse Notebooks—bridges the gap between raw cloud storage and executive-ready insights, laying a solid foundation for sustainable beekeeping research.

## ETL Project with SSIS: Uber Data Warehouse

## Project Description
This project demonstrates the implementation of an ETL (Extract, Transform, and Load) process using SQL Server Integration Services (SSIS). The primary objective is to simulate the migration of transactional data from a ride-sharing application (Uber-style) into a centralized Data Warehouse, specifically modeled for Business Intelligence (BI) and analytical reporting.

## Technologies & Tools
ETL: SQL Server Integration Services (SSIS) / Visual Studio
Source Database (Staging): SQL Server
Data Warehouse (Destination): SQL Server (OLE DB)

## Data Architecture (Dimensional Model)
The data flow is designed to feed an analytical model structured into **Dimension Tables** and **Fact Tables**.

### Dimension Tables (Dim)
* **Dim_Ciudad:** 
* **Dim_Usuario:** 
* **Dim_Conductor:**
* **Dim_MetodoPago:** 
* **Dim_EstadoViaje:**
* **Dim_EstadoPago:** 
### Fact tables (Fact)
* **Fact_RegistroUsuario:** 
* **Fact_Pago:** 
* **Fact_Calificacion:**
* **Fact_SolicitudAsignacion:**
* **Fact_Viaje:** 

## Transformaciones Principales Utilizadas
* **Derived Column:** Used to calculate new metrics (e.g., Net Profit), standardize text formats, and inject audit metadata like `LoadDate`.
* **Data Conversion:** Ensures data types from source tables align with the Data Warehouse schema (e.g., handling Unicode `DT_WSTR` conversions for global data).
* **Lookup:** Essential for maintaining referential integrity by mapping business keys to **Surrogate Keys** in the Star Schema.
* **Union All:** Consolidates multiple data streams (e.g., merging trip logs from different regional databases) into a single pipeline.
* **Sort:** Organizes data to enable efficient `Merge Join` operations and removes duplicate records during the transformation phase.
* **Conditional Split:** Routes data into different paths based on logic, such as separating "Failed Payments" for a specific error-handling log.
<img width="1837" height="882" alt="Captura de pantalla 2026-03-03 174213" src="https://github.com/user-attachments/assets/2b4a4c39-6b84-4ee0-8bad-4c09d1b9f053" />


__# House Price Analysis Data Pipeline
## Interview Practical Implementation
**Date**: 09/01/2026
**Author**: Jian Ouyang
**Platform**: Microsoft Fabric
**Architecture**: Medallion (Bronze-Silver-Gold)

---

## 🎯 BUSINESS REQUIREMENTS
1. **Bronze Layer**: Ingest raw CSV, preserve schema, validate integrity
2. **Silver Layer**: 
   - Split into HousePriceTimeSeries and Houses (Type 2 SCD)
   - Data quality: No null property_id/rooms/price, positive prices, valid month format
3. **Gold Layer**: Star schema with FactAverageHousePrice (average price over time series)
4. **Power BI**: Descriptive dashboard for data exploration

---

## 📊 DATA UNDERSTANDING
**Source File**: `house-price-timeseries.csv`
**Key Fields**:
- `property_id`: Unique property identifier
- `month`: Time period (YYYY-MM)
- `price`: Sale price
- Room-related: `bedrooms`, `bathrooms`, `guestroom`, etc.
- Property attributes: `area`, `stories`, `mainroad`, etc.

**Data Characteristics**:
- Time series data (2023-01 to 2025-12)
- Multiple properties tracked monthly
- Some properties have attribute changes over time (e.g., bedrooms change)

---

## 🏗️ ARCHITECTURE DESIGN
![Medallion Architecture Design](/Screenshots/architecture_DE.png)

---
## Fabric Workspace Overview
Workspace shows Lakehouse, Notebooks, Pipeline, Semantic Model, and Report. A screenshot is below:
![Fabric Workspace](/Screenshots/Fabric_Workspace.jpg)

---
## Dashboard Screenshots
![Dashboard Screenshots](/Screenshots/dashboard.png)

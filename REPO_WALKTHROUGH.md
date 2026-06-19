# Restaurant One Solution (ROS) - Repository Walkthrough

## Overview
This repository contains the complete data engineering, analytics, and BI solution for the Restaurant One Solution (ROS) project. It includes raw data, processed datasets, SQL schemas, ETL workflows, PowerBI dashboards, and comprehensive documentation.

---

## Directory Structure

```
.
├── data/
│   ├── raw/
│   │   ├── csv/                    # 15 raw CSV data files
│   │   │   ├── Banking.csv         # Banking transactions (18K rows)
│   │   │   ├── Cash_Up.csv         # Cash reconciliation (18K rows)
│   │   │   ├── Clients.csv         # Client reference data (31 rows)
│   │   │   ├── Countries.csv       # Country reference data (250 rows)
│   │   │   ├── Currencies.csv      # Currency reference data (5 rows)
│   │   │   ├── Deliveries.csv      # Delivery tracking (219K rows)
│   │   │   ├── Departments.csv     # Department reference (10 rows)
│   │   │   ├── Expenses.csv        # Expense tracking (18K rows)
│   │   │   ├── Orders.csv          # Order transactions (547K rows)
│   │   │   ├── Restaurants.csv     # Restaurant reference (51 rows)
│   │   │   ├── Roles.csv           # User roles (5 rows)
│   │   │   ├── Sales.csv           # Sales transactions (18K rows)
│   │   │   ├── Subscriptions.csv   # Subscription plans (5 rows)
│   │   │   ├── TaxInfo.csv         # Tax information (3 rows)
│   │   │   └── Users.csv           # User accounts (301 rows)
│   │   ├── Data Anomalies- ROS.xlsx
│   │   ├── Data Cleaning Matrix.xlsx
│   │   ├── Data Generation Strategy - ROS.xlsx
│   │   ├── Data Transformation Tracker - ROS.xlsx
│   │   ├── Key Analytics and Strategies - ROS.xlsx
│   │   └── Workflow_Testing_Report - ROS.xlsx
│   ├── processed/
│   │   ├── ROS_Dataset.xlsx        # Consolidated dataset (50MB)
│   │   └── ROS-Data Dictionary.xlsx
│   └── sql/
│       ├── ROS_DDL_MySQL.sql       # MySQL DDL schema
│       ├── ROS_LOAD_DATA.sql       # Generic data loading script
│       ├── ROS_LOAD_MySQL.sql      # MySQL-specific loading script
│       └── ROS.sql                 # Full database dump
│
├── docs/
│   ├── Data Cleaning Docket.docx
│   ├── Data Generation Docket.docx
│   ├── Solution Design Docket.docx
│   ├── Solution Design Document.pdf
│   └── Validation_Report.txt
│
├── workflows/
│   └── ROS WorkFlows.knwf          # KNIME ETL workflow
│
├── dashboards/
│   └── ROS POWERBI.pbix            # PowerBI dashboard
│
├── templates/
│   └── KNIME Workflow Logic Document - Template.docx
│
└── README.md
```

---

## Data Pipeline Flow

### 1. Raw Data Ingestion (CSV)
- **Reference Data**: Clients, Countries, Currencies, Departments, Roles, Restaurants, Subscriptions, TaxInfo, Users
- **Transactional Data**: Banking, Cash_Up, Deliveries, Expenses, Orders, Sales

### 2. Data Processing (KNIME Workflow)
The `ROS WorkFlows.knwf` contains the complete ETL pipeline:
- Data extraction from CSV sources
- Data cleaning and validation (tracked in Data Cleaning Matrix)
- Transformation logic (documented in Data Transformation Tracker)
- Anomaly detection (Data Anomalies analysis)
- Load into MySQL database

### 3. Database Layer (MySQL)
- **Schema**: `ROS_DDL_MySQL.sql` defines tables, indexes, constraints
- **Loading**: `ROS_LOAD_MySQL.sql` and `ROS_LOAD_DATA.sql` for bulk import
- **Full Dump**: `ROS.sql` contains complete database with data

### 4. Analytics & Reporting
- **PowerBI Dashboard**: `ROS POWERBI.pbix` - Interactive visualizations
- **Key Analytics**: Documented in `Key Analytics and Strategies - ROS.xlsx`
- **Processed Dataset**: `ROS_Dataset.xlsx` - Consolidated analytical dataset
- **Data Dictionary**: `ROS-Data Dictionary.xlsx` - Field definitions

---

## Documentation Guide

| Document | Purpose |
|----------|---------|
| `Solution Design Document.pdf` | High-level architecture & design decisions |
| `Solution Design Docket.docx` | Detailed design specifications |
| `Data Generation Docket.docx` | Synthetic data creation methodology |
| `Data Generation Strategy - ROS.xlsx` | Data generation rules & parameters |
| `Data Cleaning Docket.docx` | Data quality issues & remediation |
| `Data Cleaning Matrix.xlsx` | Cleaning rules per column/table |
| `Data Transformation Tracker - ROS.xlsx` | Transformation logic per field |
| `Data Anomalies- ROS.xlsx` | Identified anomalies & root causes |
| `Key Analytics and Strategies - ROS.xlsx` | Business metrics & KPI definitions |
| `Workflow_Testing_Report - ROS.xlsx` | ETL testing results & validation |
| `Validation_Report.txt` | Final data validation summary |
| `ROS-Data Dictionary.xlsx` | Complete field catalog with types |
| `KNIME Workflow Logic Document - Template.docx` | Workflow documentation template |

---

## Quick Start

### Database Setup
```bash
mysql -u root -p < data/sql/ROS_DDL_MySQL.sql
mysql -u root -p < data/sql/ROS_LOAD_MySQL.sql
# Or use full dump:
mysql -u root -p < data/sql/ROS.sql
```

### KNIME Workflow
1. Open `workflows/ROS WorkFlows.knwf` in KNIME Analytics Platform
2. Configure file paths to `data/raw/csv/`
3. Execute workflow to regenerate processed data

### PowerBI Dashboard
1. Open `dashboards/ROS POWERBI.pbix` in PowerBI Desktop
2. Update data source to point to MySQL database or `data/processed/ROS_Dataset.xlsx`

---

## Key Metrics & KPIs

- **Revenue**: Orders, Sales, Banking reconciliation
- **Operations**: Deliveries, Cash-ups, Expenses
- **Customers**: Clients, Users, Subscriptions
- **Restaurants**: Multi-location performance

---

## Data Quality Notes

- All raw CSV files profiled and documented
- Cleaning rules applied per Data Cleaning Matrix
- Anomalies tracked and resolved (see Data Anomalies)
- Validation report confirms data integrity

---

## Maintenance

- **Schema Changes**: Update `ROS_DDL_MySQL.sql` and `ROS_LOAD_MySQL.sql`
- **New Data**: Add to `data/raw/csv/` and extend KNIME workflow
- **Dashboard Updates**: Modify `ROS POWERBI.pbix` and republish
- **Documentation**: Keep docs/ in sync with data/ changes

---

## Contact & References

- Project: Restaurant One Solution (ROS)
- Primary Tools: KNIME, MySQL, PowerBI
- Data Formats: CSV, SQL, XLSX, PBIX, KNWF
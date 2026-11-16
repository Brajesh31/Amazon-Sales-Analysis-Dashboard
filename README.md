# 📊 Amazon Sales Analysis Dashboard

<p align="center">
  <strong>A Power BI sales-analysis project with tabular source data, an editable report, a PDF snapshot, and SQL exploration assets.</strong>
</p>

<p align="center">
  <a href="https://github.com/Brajesh31/Amazon-Sales-Analysis-Dashboard/stargazers"><img src="https://img.shields.io/github/stars/Brajesh31/Amazon-Sales-Analysis-Dashboard?style=for-the-badge" alt="Stars"></a>
  <a href="https://github.com/Brajesh31/Amazon-Sales-Analysis-Dashboard/issues"><img src="https://img.shields.io/github/issues/Brajesh31/Amazon-Sales-Analysis-Dashboard?style=for-the-badge" alt="Issues"></a>
  <a href="LICENSE"><img src="https://img.shields.io/github/license/Brajesh31/Amazon-Sales-Analysis-Dashboard?style=for-the-badge" alt="MIT License"></a>
  <img src="https://img.shields.io/badge/Power%20BI-Desktop-F2C811?style=for-the-badge&logo=powerbi&logoColor=black" alt="Power BI">
  <img src="https://img.shields.io/badge/SQL-MySQL%20style-4479A1?style=for-the-badge&logo=mysql&logoColor=white" alt="SQL">
</p>

---

## 📚 Table of Contents

- [Project Overview](#-project-overview)
- [Repository Contents](#-repository-contents)
- [Data at a Glance](#-data-at-a-glance)
- [Analysis Scope](#-analysis-scope)
- [Technology and Tools](#-technology-and-tools)
- [Architecture and Data Flow](#-architecture-and-data-flow)
- [Data Dictionary](#-data-dictionary)
- [Open the Power BI Report](#-open-the-power-bi-report)
- [Work with the Dataset](#-work-with-the-dataset)
- [SQL Exploration](#-sql-exploration)
- [Refresh and Reproducibility](#-refresh-and-reproducibility)
- [Data Quality and Validation](#-data-quality-and-validation)
- [Security and Responsible Use](#-security-and-responsible-use)
- [Development Workflow](#-development-workflow)
- [Testing and QA](#-testing-and-qa)
- [Deployment and Sharing](#-deployment-and-sharing)
- [Limitations and Known Gaps](#-limitations-and-known-gaps)
- [Documentation](#-documentation)
- [Contributing](#-contributing)
- [License and Maintainer](#-license-and-maintainer)

## 📌 Project Overview

This repository contains a Microsoft Power BI sales-analysis dashboard project using a combined product-oriented dataset. The deliverables include an editable Power BI Desktop report, a PDF export, CSV and Excel versions of the source data, a short MySQL-style SQL exploration file, and supporting presentation images.

The intended workflow is to inspect and transform the supplied tabular data, build or review report visuals and measures in Power BI, validate aggregations against the source, and export a static report snapshot for sharing.

**Important data-provenance note:** the repository is an independent analysis project. The dataset should not be described as official Amazon financial, order-management, or operational reporting without verified provenance and authorization. Values in the source file are analytical inputs, not independently authenticated business facts.

## 📦 Repository Contents

| File | Type | Purpose |
|---|---|---|
| `Amazon.pbix` | Power BI binary | Editable report, model, queries, and visuals |
| `Amazon.pdf` | PDF | Static report export |
| `Amazon_Combined_Data.csv` | CSV | Flat source dataset |
| `Amazon_Combined_Data.xlsx` | Excel workbook | Spreadsheet representation of source data |
| `Amazon Database.sql` | SQL | Minimal MySQL-style database selection and query example |
| `Project_Img.png` | PNG | Project/dashboard presentation image |
| `Amazon Background.jpg` | JPEG | Presentation background asset |
| `Amazon-Logo.png` | PNG | Logo image used for presentation |

The Power BI report is the interactive artifact. The PDF is a snapshot and cannot refresh data or respond to slicers. CSV and XLSX are two representations of the source data and may not necessarily be the exact file currently selected by the PBIX model. Verify the report's configured source path before refreshing.

## 📈 Data at a Glance

The repository README and source metadata describe a combined dataset of approximately **89,082 rows and six columns**.

| Source field | Description |
|---|---|
| `Product Category` | Product category label |
| `Product Description` | Product description text |
| `Price(Dollar)` | Price-like value expressed in dollar units |
| `Number of  reviews` | Review-count-like value, including irregular spacing in the header |
| `Shipment` | Shipment/destination descriptive text |
| `Order Date` | Date-like source value stored as text in the CSV |

The CSV/XLSX are not guaranteed to be a clean fact table. The field names and values need explicit typing, normalization, and validation before making quantitative claims.

## 🔍 Analysis Scope

The supplied fields can support exploratory analysis such as:
- product category distribution;
- price distribution and summary statistics;
- review-count distribution;
- descriptive comparisons across shipment text values;
- time-based summaries after parsing the order date;
- comparisons across categories and selected price/review bands.

The actual measures, filters, relationships, visual titles, and slicer configuration are stored in the PBIX binary. They have not been exhaustively inspected as text in this maintenance pass. Consequently, this README avoids inventing exact dashboard visuals, KPI totals, sales revenue, order counts, or business conclusions.

A key distinction: a price field and a review count do not, by themselves, establish sales volume, revenue, profit, conversion, or order fulfillment. Treat the analysis as a product-data exploration unless the underlying model contains verified transaction measures.

## 🧰 Technology and Tools

| Tool / Format | Role |
|---|---|
| Microsoft Power BI Desktop | Report authoring, data model, visualizations, refresh |
| Power Query | Data-source connection and transformation within the PBIX, subject to report configuration |
| CSV | Plain-text tabular source |
| Microsoft Excel | Tabular inspection and alternative source representation |
| MySQL-style SQL | Optional database exploration example |
| PDF | Static export for non-interactive review |
| Git / GitHub | Versioning, documentation, issue tracking, and release history |

This repository is primarily a Power BI artifact. It does not currently provide a Python or JavaScript application, a public web dashboard, or an automated data pipeline.

## 🏗️ Architecture and Data Flow

```text
Amazon_Combined_Data.csv       Amazon_Combined_Data.xlsx
          |                               |
          +---------------+---------------+
                          |
                 Power BI Desktop
                    Amazon.pbix
                          |
             Model / transformations /
                 report visuals
                          |
                Exported Amazon.pdf

Optional SQL exploration:
Amazon Database.sql
        |
        v
MySQL-compatible database
        |
        v
Expected table: amazon
(schema and import are not supplied)
```

The SQL example is independent of the PBIX data-refresh path. The SQL file creates/selects a database and queries a table named `amazon`, but it does not create that table or import either source file.

See [Architecture](docs/architecture.md), [Data Lineage](docs/data-lineage.md), and [Database Guide](docs/database.md).

## 🧾 Data Dictionary

The data dictionary records the source field names, recommended analytical types, cleaning rules, and cautions. See [docs/data-dictionary.md](docs/data-dictionary.md).

| Field | Recommended analytical type | Main caution |
|---|---|---|
| Product Category | Text/category | Trim whitespace and standardize labels |
| Product Description | Text | Not a stable unique product key |
| Price(Dollar) | Decimal | Parse currency/separators and confirm units |
| Number of  reviews | Whole number | Normalize header and parse separators |
| Shipment | Text/category | Semantics need confirmation before geographic or delivery analysis |
| Order Date | Date | Parse locale and invalid values explicitly |

## 🖥️ Open the Power BI Report

### Prerequisites
- Microsoft Power BI Desktop.
- Access to the repository files.
- A supported Windows environment for authoring in Power BI Desktop.

### Steps
1. Clone or download this repository.
2. Open `Amazon.pbix` in Power BI Desktop.
3. Review the model and Power Query steps.
4. Open data source settings and identify the currently configured source.
5. If the original path is unavailable, reconnect to the intended CSV or XLSX file.
6. Apply transformations only after reviewing the source types and cleaning requirements.
7. Refresh the model.
8. Validate totals against a raw-data sample.
9. Save a working copy before editing the tracked PBIX.
10. Export a new PDF only after verifying the report state.

Do not overwrite the source PBIX without keeping a known-good copy. Record the Power BI Desktop version, source file, transformations, refresh date, and filters used.

For more detail, read [Installation](docs/installation.md) and [Report Guide](docs/report-guide.md).

## 📂 Work with the Dataset

### CSV
The CSV can be opened in Excel, Power BI, or a data-processing tool. Preserve the original file as an immutable raw copy. Do not silently change encoding, delimiter, row order, or field names.

### XLSX
The workbook is an alternative tabular representation. Confirm sheet names, headers, formula cells, and data types before using it as a report source. Do not assume CSV and XLSX are byte-identical or semantically identical without comparison.

### Recommended workflow
1. Keep original data unchanged.
2. Profile row counts and headers.
3. Normalize column names in a separate transformation layer.
4. Trim category/shipment strings.
5. Parse price and review fields with explicit locale rules.
6. Parse order dates and record failed conversions.
7. Inspect nulls, duplicates, and outliers.
8. Validate output row counts and aggregates.
9. Point the Power BI model at the approved source.
10. Record the transformation and refresh details.

See [Data Preparation](docs/data-preparation.md) and [Data Quality](docs/data-quality.md).

## 🗄️ SQL Exploration

The file `Amazon Database.sql` currently contains:

```sql
CREATE DATABASE Amazon;
USE Amazon;
SHOW TABLES;

SELECT * FROM amazon;
```

This is only a database selection and table-query example. It does **not**:
- create the `amazon` table;
- define its column schema;
- import the CSV/XLSX;
- clean or normalize source values;
- define keys or indexes;
- create a Power BI connection.

Running the final query on a fresh database will fail until a table named `amazon` has been created and loaded. Use a disposable/local database for exploration and review SQL before execution. See [SQL Workflow](docs/sql-workflow.md).

## 🔄 Refresh and Reproducibility

The PBIX model may contain Power Query steps, relationships, measures, and visual settings that are not represented by the SQL file. Keep a written record of:
- Power BI Desktop version;
- source file name and checksum, where practical;
- source worksheet/table or CSV path;
- transformation steps and type conversions;
- refresh timestamp;
- filters/slicers applied for exported snapshots;
- any changed measures, relationships, or calculated columns.

The PDF export should be treated as a timestamped snapshot of a specific PBIX state, not a live report.

## ✅ Data Quality and Validation

Before using the dashboard for conclusions, validate:
- source row count and six expected fields;
- category spelling, casing, and whitespace;
- price parsing, unit, range, and missing values;
- review count parsing and non-negative values;
- shipment semantics and inconsistent labels;
- order date parsing and locale;
- duplicate records and whether duplicate rows are meaningful;
- aggregate totals before and after Power Query transformations;
- filters and relationship effects in the report.

Do not equate product price with sales revenue. Do not infer shipment completion, geography, or delivery performance solely from an unnormalized shipment text field.

## 🔐 Security and Responsible Use

- Keep Power BI credentials, gateway credentials, and connection strings out of Git.
- Review hidden pages, hidden columns, model metadata, and source paths before sharing a PBIX.
- Do not commit private customer, order, or commercially sensitive exports.
- Confirm redistribution rights for source data, logos, images, and report assets.
- Avoid using Amazon branding in a way that suggests official endorsement.
- Share reports only with an audience authorized to access the underlying data.

See [Security Guide](docs/security.md).

## 🧑‍💻 Development Workflow

Changes to report visuals and data modeling should be made in Power BI Desktop. CSV/XLSX edits should be handled as data changes with clear provenance and validation. SQL edits should document the target dialect and whether a query is read-only or mutating.

The PBIX file is binary and cannot be meaningfully reviewed with ordinary line-by-line diffs. Include screenshots or exported previews for visual changes and explain the measure/model impact. See [Development](docs/development.md).

## 🧪 Testing and QA

There is no automated Power BI semantic-model test suite or ETL pipeline in this repository. QA is therefore a documented manual process:
- open the PBIX;
- confirm data-source settings;
- refresh from a clean copy;
- inspect query errors;
- validate data types and row counts;
- reconcile key measures against independently calculated source summaries;
- test slicers, page navigation, and cross-filter behavior;
- export PDF and compare it with the saved PBIX state.

See [Testing](docs/testing.md).

## 🚀 Deployment and Sharing

Use a controlled Power BI workspace and apply least-privilege dataset/report permissions. Configure refresh credentials through approved Power BI data-source settings or gateway administration, not by committing credentials. Review the exported PDF and PBIX metadata for confidential content before distribution.

This repository does not contain an automated Power BI Service deployment pipeline. See [Deployment](docs/deployment.md).

## ⚠️ Limitations and Known Gaps

- The source data's provenance and official relationship to Amazon are not verified here.
- The PBIX is a binary report; its measures, visuals, and full transformation graph were not independently reconstructed in this documentation.
- The SQL file assumes an `amazon` table that it does not create or populate.
- No schema or reproducible SQL import pipeline is included.
- The CSV/XLSX active PBIX source path must be checked in Power BI Desktop.
- Header names and data types require normalization.
- There is no automated model-level test suite.
- Third-party asset/data licenses require separate verification.

Documentation cannot substitute for validating the report model or source data.

## 📚 Documentation

| Guide | Description |
|---|---|
| [Documentation Index](docs/README.md) | Full guide list |
| [Installation](docs/installation.md) | Power BI setup and first open |
| [Architecture](docs/architecture.md) | Files and data flow |
| [Report Guide](docs/report-guide.md) | Navigating and reviewing PBIX/PDF |
| [Data Dictionary](docs/data-dictionary.md) | Source columns and types |
| [Data Preparation](docs/data-preparation.md) | Cleaning and transformation workflow |
| [Data Quality](docs/data-quality.md) | Validation and analytical cautions |
| [Data Lineage](docs/data-lineage.md) | Source-to-report traceability |
| [Database](docs/database.md) | SQL/table boundary and schema guidance |
| [SQL Workflow](docs/sql-workflow.md) | Safe MySQL exploration |
| [Development](docs/development.md) | Making report and data changes |
| [Testing](docs/testing.md) | Manual validation checklist |
| [Deployment](docs/deployment.md) | Power BI workspace and sharing |
| [Security](docs/security.md) | Credentials, privacy, and responsible use |
| [Troubleshooting](docs/troubleshooting.md) | Common source/refresh/report problems |
| [API](docs/api.md) | Clarifies the lack of a network API |
| [FAQ](docs/faq.md) | Common questions |
| [Release Process](docs/release-process.md) | Releasing verified report artifacts |
| [Glossary](docs/glossary.md) | BI and data terminology |
| [Asset Licensing](docs/asset-licensing.md) | Data/logo/image licensing boundary |

## 🤝 Contributing

Read [CONTRIBUTING.md](CONTRIBUTING.md) before submitting changes. Keep source-data changes traceable, document PBIX transformations, provide screenshots for report changes, and never add credentials or unlicensed assets.

## 📄 License and Maintainer

Project-authored repository material is provided under the MIT License. Third-party datasets, images, logos, and trademarks remain subject to their own terms. See [LICENSE](LICENSE).

Maintained by **Brajesh Kumar**: [@Brajesh31](https://github.com/Brajesh31).

Last updated: 2026-11-16 05:21 UTC

# 📚 Documentation Index

This directory provides operational and analytical documentation for the Amazon Sales Analysis Dashboard repository. It describes the Power BI report and the supplied source artifacts while distinguishing inspected facts from assumptions that still need confirmation in Power BI Desktop.

## Getting Started

| Guide | What it covers |
|---|---|
| [Installation](installation.md) | Power BI Desktop prerequisites, repository access, and opening the report |
| [Report Guide](report-guide.md) | PBIX versus PDF, navigating report pages, filters, and export review |
| [Architecture](architecture.md) | Source artifacts and report/data flow |
| [Development](development.md) | Safe changes to the PBIX, data, and SQL |
| [Release Process](release-process.md) | Validation and release checklist |

## Data and SQL

| Guide | What it covers |
|---|---|
| [Data Dictionary](data-dictionary.md) | Field-level definitions, types, units, and caveats |
| [Data Preparation](data-preparation.md) | Profiling, normalization, typing, and transformation |
| [Data Quality](data-quality.md) | Completeness, duplicate, range, and reconciliation checks |
| [Data Lineage](data-lineage.md) | How files relate and how to record provenance |
| [Database](database.md) | Current SQL/database boundary and required schema work |
| [SQL Workflow](sql-workflow.md) | Safe MySQL setup and import planning |

## Operations and Governance

| Guide | What it covers |
|---|---|
| [Configuration](configuration.md) | Data-source settings and environment/credential boundaries |
| [Testing](testing.md) | Manual report, refresh, and data validation |
| [Deployment](deployment.md) | Workspace publishing and controlled sharing |
| [Security](security.md) | Confidentiality, access, and safe handling |
| [Asset Licensing](asset-licensing.md) | Source-data, logo, font, and image rights |
| [API](api.md) | Confirms that no HTTP API is included |
| [Glossary](glossary.md) | Business intelligence and data terms |
| [Troubleshooting](troubleshooting.md) | Refresh, parsing, SQL, and export problems |
| [FAQ](faq.md) | Common use and project-scope questions |

## Repository Policies

- [Root README](../README.md)
- [Contributing](../CONTRIBUTING.md)
- [Code of Conduct](../CODE_OF_CONDUCT.md)
- [Security Policy](../SECURITY.md)
- [Support](../SUPPORT.md)
- [Changelog](../CHANGELOG.md)
- [Roadmap](../ROADMAP.md)
- [MIT License](../LICENSE)

## Recommended Reading Paths

**Dashboard user:** Installation, Report Guide, FAQ.

**Data analyst:** Data Dictionary, Data Preparation, Data Quality, Data Lineage.

**SQL user:** Database, SQL Workflow, Security.

**Report maintainer:** Architecture, Configuration, Development, Testing, Deployment, Release Process.

## Documentation Rules

- Describe actual files and observed columns, not invented business metrics.
- Do not assume the PBIX uses CSV or XLSX until its active source path is confirmed.
- Distinguish product price from actual sales revenue.
- Do not infer official Amazon data provenance from the repository name.
- Do not invent the unseen PBIX measures, visuals, relationships, or filter behavior.
- Keep credentials and private exports out of the repository.
- Update the affected guides whenever data fields, query steps, report structure, or source files change.

Maintained by Brajesh Kumar.


# Amazon Sales Analysis Dashboard

This repository contains a Power BI sales-analysis project backed by a combined Amazon product dataset. It includes the editable Power BI report, an exported PDF preview, source CSV/XLSX data, a small SQL exploration script, and presentation assets.

## Contents

| File | Purpose |
| --- | --- |
| `Amazon.pbix` | Editable Power BI Desktop report |
| `Amazon.pdf` | Exported report snapshot |
| `Amazon_Combined_Data.csv` | Flat source dataset with 89,082 rows and six columns |
| `Amazon_Combined_Data.xlsx` | Spreadsheet copy of the source data |
| `Amazon Database.sql` | MySQL-style database selection and exploration script |
| `Project_Img.png`, `Amazon Background.jpg`, `Amazon-Logo.png` | Dashboard presentation assets |

The source columns are `Product Category`, `Product Description`, `Price(Dollar)`, `Number of  reviews`, `Shipment`, and `Order Date`. The sample data contains product descriptions, prices, review counts, destination text, and dates; treat it as external or unverified data rather than a source of official Amazon financial reporting.

## Open the dashboard

Install Power BI Desktop, open [`Amazon.pbix`](./Amazon.pbix), and inspect the data source settings. If Power BI reports a missing file, reconnect the model to [`Amazon_Combined_Data.xlsx`](./Amazon_Combined_Data.xlsx) or the CSV using the path configured in the report.

The PDF is a static export and cannot be refreshed. Use the PBIX file for filters, model inspection, and updated visuals.

## SQL exploration

[`Amazon Database.sql`](./Amazon%20Database.sql) creates/selects a database named `Amazon`, selects it, lists tables, and queries an `amazon` table. It does not create or load that table. A complete SQL workflow therefore requires an authorized MySQL instance and an explicit import/mapping step.

## Data quality considerations

- Numeric fields may contain commas, currency formatting, or mixed values and should be typed explicitly before aggregation.
- `Order Date` is stored as text in the CSV and needs date parsing.
- Category values may contain trailing whitespace.
- Product descriptions are long text and should not be treated as unique product IDs without a separate key.
- Shipment text is descriptive, not a normalized geography or logistics status.

## Reproducibility

Record the Power BI Desktop version, source file used, transformations, refresh date, and any filters applied when sharing a report. Do not publish customer-identifying, credential, or commercially sensitive data.

See [`docs/database.md`](./docs/database.md), [`docs/development.md`](./docs/development.md), and [`docs/troubleshooting.md`](./docs/troubleshooting.md) for details.

## License

Repository documentation and project-authored material are released under the MIT License. Third-party data, logos, images, and trademarks remain subject to their own terms. See [`LICENSE`](./LICENSE).

Last updated: 2026-10-17 18:14 UTC

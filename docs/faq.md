# FAQ

## Is this official Amazon data?

The repository contains an analysis project and a source dataset, not an official Amazon reporting feed. Verify provenance, licensing, and accuracy before relying on results.

## Why are there both CSV and XLSX files?

They are alternative tabular representations of the source. The PBIX report may be connected to one specific file; document and verify the active source before refreshing.

## Can the PDF be refreshed?

No. It is a static export. Open the PBIX report to refresh data and interact with visuals.

## Does the SQL file create the data table?

No. It creates/selects a database and queries an assumed `amazon` table. The schema and import process still need to be defined.

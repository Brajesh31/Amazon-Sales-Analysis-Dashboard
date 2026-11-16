# Testing and Quality Assurance

## Current Automation Status

The repository primarily contains binary Power BI artifacts and data files. It currently has no committed automated ETL test suite, Power BI semantic-model test framework, or SQL integration test environment. CI can validate repository files and links, but it cannot prove that the PBIX opens, refreshes, or renders correctly.

## Source Data Checks

Before refreshing a report, verify expected columns and row count, CSV encoding/delimiter, workbook sheet/header structure, nulls/blanks, numeric conversion, date parsing with explicit locale, category/shipment variants, and duplicate candidates. Determine the row grain before deduplication.

## Power Query Checks

In Power BI Desktop, refresh every query, confirm the source path, inspect Applied Steps, identify type-conversion errors, check rows removed by filters, verify intermediate/final row counts, and make sure shared artifacts do not use a personal local path.

## Model Checks

Inspect tables, relationships, cardinality, filter direction, calculated columns, DAX measures, hidden fields, aggregation defaults, and formatting. Reconcile important calculations against independent source summaries. Do not assume measure names imply correct business definitions.

## Visual Checks

For each page, review titles, labels, axis scales, number formats, slicer behavior, cross-filtering, reset behavior, totals, error/blank visuals, and readability. The exact page inventory must be read from the PBIX; this document does not invent page names or visuals.

## PDF Export Checks

Save the validated PBIX, apply the intended filter state, export the PDF, verify page count/order and visual rendering, and record export/refresh date and filter context.

## SQL Checks

The current SQL file queries a table it does not create. Test any schema/import additions in a disposable database and validate types, row counts, and sample records before production use.

## Evidence Record

Record source filename/version, refresh date, Power BI version, row counts, conversion errors, aggregate reconciliations, filter scenarios, PDF export status, and reviewer. Do not claim a check passed if it was not performed.

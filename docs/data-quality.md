# ✅ Data Quality and Analytical Validation

## Purpose

Data quality checks protect the dashboard from incorrect aggregations caused by parsing errors, inconsistent labels, duplicates, missing values, and unverified business semantics.

The project includes a CSV/XLSX dataset and a Power BI report. This guide defines controls to run during report refresh and before publishing a conclusion.

## 1. Structural Checks

- Confirm six expected source fields.
- Confirm row count against the approved source version.
- Check for renamed, missing, duplicated, or reordered headers.
- Verify CSV delimiter and encoding.
- Confirm workbook sheet/table names and headers.
- Record source file version or checksum where practical.

## 2. Completeness Checks

Calculate blank/null counts for every field. Investigate rather than automatically deleting incomplete records. For example, a missing review count may mean unknown, not zero.

## 3. Category Checks

Trim whitespace and profile distinct category values. Compare near-duplicates and spelling variants. Build a reviewed mapping table only after confirming equivalence. Preserve original values for audit.

## 4. Price Checks

Validate conversion to decimal and examine:
- null/blank count;
- non-numeric count;
- zero and negative values;
- minimum and maximum;
- extreme outliers;
- currency consistency.

Do not infer sales or revenue totals from price alone.

## 5. Review Count Checks

Verify numeric parsing, non-negative values, integer type, and separator conventions. Preserve missing and malformed values distinctly. Avoid silent text-to-zero conversion.

## 6. Shipment Checks

Inspect actual values and confirm what they represent. A descriptive shipment text field should not be used as a delivery-status or geographic measure unless the semantics and categories are known.

## 7. Date Checks

Use explicit locale when parsing `Order Date`. Track invalid conversions. Compare earliest/latest dates with the expected reporting period. Investigate dates in the future or outside the source context.

## 8. Duplicate Checks

Determine row grain before deduplication. Repeated product descriptions can be valid. Exact duplicate rows should be investigated with source context rather than removed automatically.

## 9. Reconciliation

For selected categories and date ranges, calculate independent totals/counts from the raw source and compare with Power BI results after filters are understood. Confirm that relationships or visual interactions are not multiplying rows.

## 10. Publication Gate

Before sharing:
- no unexplained query errors;
- all type conversions reviewed;
- source and transformed row counts reconciled;
- key measures independently recomputed;
- filters/slicers tested;
- PDF matches the saved PBIX state;
- no confidential or unauthorized data is present;
- data provenance and limitations are visible to consumers.

## 11. Evidence

Keep a refresh validation record containing source version, refresh date, row counts, rejected values, key aggregate checks, Power BI version, and reviewer. Do not claim a data-quality pass unless checks were actually run.

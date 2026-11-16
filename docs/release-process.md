# Release Process

## 1. Release Contents

A dashboard release may include a validated PBIX, matching PDF export, documented source data version, documentation/changelog, and required presentation assets with verified rights. Avoid temporary exports, personal paths, credentials, or local working files.

## 2. Source Validation

Confirm source file/version, schema and row count, provenance/usage rights, Power BI Desktop version, Power Query/model changes, and key measures against independent source calculations.

## 3. Report Validation

Open the PBIX in Power BI Desktop, refresh all queries, inspect every report page, test slicers/filter behavior, review units/labels, and check for errors. A successful repository CI workflow is not a substitute for this review.

## 4. PDF Export

Save the validated PBIX, set intended filters, export the PDF, and inspect order, layout, legends, labels, and truncation. Record refresh/export date and filter context.

## 5. SQL Review

Confirm target dialect, schema dependency, permissions, and whether statements mutate data. Test in a disposable database. The current script is not a full import solution.

## 6. Documentation and Changelog

Update README, data dictionary, lineage, report guide, and relevant operational pages when source/report changes. Add verified work to Unreleased and use a dated version heading for an actual release.

## 7. Distribution Review

Confirm sharing permissions, data/assets license, PBIX hidden content, and absence of private identifiers or credentials. Keep a previous known-good release.

## 8. Rollback

If a publication contains incorrect data, broken refresh, or misleading visuals, restore the previous validated PBIX/PDF and document the defect before republishing.

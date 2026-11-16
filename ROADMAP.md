# 🗺️ Roadmap

This roadmap describes potential improvements. Items are not implemented or committed delivery dates unless separately verified.

## 🔴 Priority 1: Data Governance and Reproducibility

- [ ] Verify dataset source, provenance, and permitted use.
- [ ] Confirm the active PBIX source path and document query lineage.
- [ ] Normalize field names in the transformation layer.
- [ ] Validate price/review data types and date locale.
- [ ] Record row counts and quality metrics for each report refresh.
- [ ] Verify rights for bundled logos and presentation images.

## 🟠 Priority 2: SQL and Data Pipeline

- [ ] Define an explicit staging schema for the six source fields.
- [ ] Add a documented CSV/XLSX import workflow.
- [ ] Capture invalid rows and type-conversion exceptions.
- [ ] Add reconciliation queries for row counts and aggregates.
- [ ] Document source-to-report lineage.
- [ ] Define indexes only after query patterns and table grain are known.

## 🟡 Priority 3: Power BI Model Documentation

- [ ] Inventory report pages, visuals, and slicers from the PBIX.
- [ ] Document measures and their business definitions.
- [ ] Document relationships and filter directions.
- [ ] Add screenshots with report refresh date and filter context.
- [ ] Add report/model validation evidence.

## 🟢 Priority 4: Release and Automation

- [ ] Introduce reproducible data-quality scripts where practical.
- [ ] Add a validated refresh/release checklist.
- [ ] Evaluate Power BI deployment automation only after credentials and permissions are designed.
- [ ] Automate safe documentation and artifact checks.
- [ ] Publish release checksums and source lineage records.

## Definition of Done

A roadmap item is complete only when implemented, reviewed, validated against source/report behavior, documented, and checked for data/license/security implications.

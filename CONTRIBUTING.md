# 🤝 Contributing to Amazon Sales Analysis Dashboard

Thank you for helping improve the dashboard, its data quality, documentation, and reproducibility.

## Project Scope

This repository contains a Power BI Desktop report, a static PDF export, CSV/XLSX source data, an optional SQL exploration script, and presentation assets. It is not an official Amazon reporting feed unless its provenance and authorization are independently verified.

## Before You Begin

- Read the [README](README.md) and [Documentation Index](docs/README.md).
- Identify whether the change affects the PBIX, source data, SQL, PDF, or supporting docs.
- Keep raw data unchanged unless the source change is intentional and documented.
- Do not add credentials, private exports, customer identifiers, or unlicensed assets.
- Check for existing issues and avoid overlapping work.

## Power BI Contributions

For a report change:
1. Record the Power BI Desktop version.
2. Keep a backup of the current PBIX.
3. Inspect the active source path and Power Query steps.
4. Describe all changed pages, visuals, measures, columns, and relationships.
5. Validate affected totals independently against source data.
6. Test slicers and cross-filter behavior.
7. Include before/after screenshots where possible.
8. Export a new PDF if the checked-in snapshot is expected to match the report.

PBIX is binary, so normal line-based diffs do not explain visual/model changes.

## Data Contributions

- Preserve source provenance and source version.
- Record schema, row count, types, locale, and date format.
- Do not silently replace invalid values with zero.
- Do not remove duplicates without understanding row grain.
- Keep rejected/invalid values visible for review.
- Reconcile aggregates after transformation.
- Update the data dictionary, quality guide, and lineage.

## SQL Contributions

State the SQL dialect and schema dependency. The current SQL file queries an `amazon` table but does not create/import it. Test new schema/import logic in a disposable database and identify whether statements are read-only or mutating.

## Documentation Contributions

Keep field names and commands aligned with repository files. Do not invent exact Power BI measures, page names, API endpoints, or database objects. Mark assumptions and unverified details clearly.

## Pull Request Checklist

- [ ] The scope and rationale are clear.
- [ ] Raw data and source lineage are preserved.
- [ ] PBIX changes were opened/refreshed in Power BI Desktop.
- [ ] Key metrics were independently validated.
- [ ] PDF export is consistent where applicable.
- [ ] SQL changes were reviewed and tested safely.
- [ ] Screenshots/evidence are included for report changes.
- [ ] Documentation and changelog are updated.
- [ ] No credentials, confidential records, or unlicensed assets were added.

## License

Repository-authored contributions are subject to the project license. Third-party data and assets may have separate terms; verify them independently.

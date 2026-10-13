# Development

For PBIX changes, use a consistent Power BI Desktop version, refresh from a controlled copy of the source, and document query transformations and model changes. Validate totals against the source before publishing.

For CSV/XLSX changes, preserve the header contract unless the PBIX queries are updated at the same time. Avoid manually editing binary report files outside Power BI Desktop.

For SQL changes, target a documented dialect, qualify tables, avoid destructive statements by default, and test read-only queries against a disposable database.

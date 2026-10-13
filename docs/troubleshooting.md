# Troubleshooting

## PBIX source cannot be found

Open Power Query or data-source settings and reconnect the model to the intended CSV/XLSX path. Avoid embedding a personal absolute path in a shared report.

## Refresh produces incorrect totals

Check numeric parsing, currency symbols, comma-separated review counts, duplicate rows, trailing category whitespace, and date locale. Compare a small sample with the raw CSV.

## SQL table does not exist

The committed SQL does not create or import the `amazon` table. Load a reviewed schema into a disposable database first, then run the read-only exploration statements.

## PDF differs from PBIX

The PDF is a point-in-time export. Re-export it after changes and record the report refresh date and filters used.

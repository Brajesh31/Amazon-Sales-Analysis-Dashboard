# 🗄️ SQL Exploration Workflow

## 1. Current SQL File

The repository's `Amazon Database.sql` contains:

```sql
CREATE DATABASE Amazon;
USE Amazon;
SHOW TABLES;
SELECT * FROM amazon;
```

This script creates/selects the database, lists tables, and queries an assumed table. It does not create the `amazon` table, define columns, load the CSV/XLSX, or clean data.

On a fresh database, the final query will fail until the table has been created and populated.

## 2. Use a Safe Environment

Use an authorized local or disposable MySQL-compatible database. Do not use production credentials or run unreviewed scripts against a live system.

Confirm server version and SQL dialect before adapting statements.

## 3. Define a Schema Before Import

The six documented raw fields need explicit types and validation. A recommended starting point is:

| Field | Suggested SQL type | Note |
|---|---|---|
| Product Category | `VARCHAR(255)` | Trim and standardize separately |
| Product Description | `TEXT` | Not necessarily unique |
| Price(Dollar) | `DECIMAL(12,2)` | Confirm currency/scale first |
| Number of reviews | `INT` | Parse separators, validate non-negative |
| Shipment | `VARCHAR(500)` | Confirm meaning before normalization |
| Order Date | `DATE` | Parse using known source locale |

This is a schema design suggestion, not a schema currently committed to the repository. Before production, determine the record grain and add a stable primary key if available.

## 4. Import Process

A complete import procedure should:
1. Preserve the raw CSV/XLSX.
2. Validate delimiter, encoding, header row, and row count.
3. Create a table with reviewed types.
4. Import into a staging table.
5. capture malformed rows rather than silently dropping them;
6. normalize headers, dates, prices, and counts;
7. reconcile staging and final row counts;
8. record import timestamp and source version.

No import statement or script is currently supplied.

## 5. Query Safely

Prefer explicit column selection over `SELECT *` for repeatable analysis. Use read-only queries for exploration. Add `LIMIT` when previewing large tables and avoid destructive commands unless the task explicitly requires them and a backup exists.

## 6. Power BI Connection

A MySQL-loaded table is a separate source path from CSV/XLSX unless the PBIX is configured to use that database. Inspect Power BI data source settings and document the actual connection. Do not assume the SQL file automatically feeds the report.

## 7. Production Readiness

Before using SQL as a repeatable pipeline, add documented schema DDL, import procedure, validation queries, indexes, access control, backup/restore procedure, and a refresh schedule. Keep secrets outside the repository.

# Configuration and Data Source Settings

## Repository Environment

The committed `.env.example` states that no runtime environment variables are required by the dashboard files. There is no Python/Node application runtime here that loads dotenv. Do not add Power BI passwords, gateway credentials, access tokens, or connection strings to the repository.

## PBIX Data Sources

The active source path used by `Amazon.pbix` must be verified in Power BI Desktop. The repository contains both CSV and XLSX versions of the dataset, but the report may reference only one of them or another source configured inside the PBIX.

To inspect:
1. Open the PBIX in Power BI Desktop.
2. Open data source settings.
3. Inspect Power Query source steps.
4. Record connector type and file path.
5. Confirm the referenced file exists.
6. Reconnect to an approved copy if needed.
7. Refresh and review all query errors.

## Shared Paths

Avoid hard-coded personal absolute paths in shared reports. A future improvement could use a documented Power Query parameter or approved shared storage location. The repository does not currently define a portable path parameter.

## Power BI Service Credentials

For a published report, configure credentials and gateway settings within approved Power BI service controls. Keep privileged values out of Git, PBIX comments, and screenshots.

## SQL Configuration

The SQL example assumes a MySQL-style database named `Amazon`. It includes no host, username, password, connection string, or import configuration. Do not invent or commit those values.

## Refresh Record

For each report refresh, record source file/version, Power BI Desktop version, refresh timestamp/status, query errors, row count before/after transformation, and filters used for export.

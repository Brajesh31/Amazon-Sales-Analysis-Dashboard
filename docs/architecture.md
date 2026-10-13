# Architecture

The repository combines a binary Power BI report, tabular source data, a SQL exploration script, and presentation assets.

```text
Amazon_Combined_Data.csv / .xlsx
              │
              ▼
       Amazon.pbix model ──► Power BI visuals
              │
              └────────────► Amazon.pdf export

Amazon Database.sql ──► optional MySQL exploration
```

The SQL script is not the ingestion path for the PBIX model and currently assumes an `amazon` table that it does not create.

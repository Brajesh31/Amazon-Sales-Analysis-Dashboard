# Database and data model

The supplied SQL script expects a MySQL-style database named `Amazon` and an `amazon` table:

```sql
CREATE DATABASE Amazon;
USE Amazon;
SHOW TABLES;
SELECT * FROM amazon;
```

It does not define the table schema or import the CSV/XLSX. The six source columns should be normalized before loading:

| Source column | Recommended type |
| --- | --- |
| `Product Category` | `VARCHAR` or dimension key |
| `Product Description` | `TEXT` |
| `Price(Dollar)` | `DECIMAL(12,2)` |
| `Number of  reviews` | integer after removing separators |
| `Shipment` | `VARCHAR` or normalized shipping dimension |
| `Order Date` | `DATE` |

Add a stable row or product/order key before treating records as facts. Preserve the raw source separately from transformed tables.

# 🔗 Data Lineage and Source Traceability

## 1. Repository Artifacts

The repository contains several related files, but they serve different roles:

| Artifact | Role | Relationship |
|---|---|---|
| `Amazon_Combined_Data.csv` | Flat tabular source | Candidate PBIX input |
| `Amazon_Combined_Data.xlsx` | Workbook copy | Alternative tabular source |
| `Amazon.pbix` | Power BI report/model | Contains report configuration, queries, model, visuals |
| `Amazon.pdf` | Static export | Snapshot generated from a PBIX/report state |
| `Amazon Database.sql` | SQL exploration | Independent optional database query example |
| `Project_Img.png` | Presentation image | Repository visual asset |
| `Amazon Background.jpg` | Background image | Presentation asset |
| `Amazon-Logo.png` | Logo image | Branding/presentation asset |

## 2. Known Relationships

The repository description says the PBIX is backed by the combined Amazon product dataset. The exact active source path and Power Query transformation chain must be confirmed in Power BI Desktop. The PDF is described as an exported snapshot. The SQL script is not established as the PBIX ingestion mechanism.

## 3. SQL Boundary

The SQL file creates/selects a database named `Amazon` and then queries `amazon`. It does not define or populate the table. Any imported SQL table is therefore a separate downstream copy unless the PBIX's source settings show otherwise.

## 4. Recommended Lineage Record

For each report version, record:

| Lineage attribute | Example information to record |
|---|---|
| Source artifact | CSV or XLSX filename |
| Source version | Git commit or file checksum |
| Ingestion method | Power Query file connector or database |
| Query transformations | Header rename, trim, type conversion, filters |
| Model objects | Tables, relationships, measures |
| Report output | PBIX commit and exported PDF |
| Refresh | Timestamp and status |
| Validation | Row counts and independent measure checks |
| Owner/reviewer | Responsible maintainer |

## 5. Source Change Procedure

1. Preserve the existing raw source.
2. Add the new source as a separately versioned artifact.
3. Compare schema and row counts.
4. Review changed values and data types.
5. Update Power Query and model references.
6. Validate all dependent measures and visuals.
7. Export a new PDF.
8. Record the source-to-report lineage.
9. Update documentation and changelog.

## 6. Provenance Limitations

The repository name does not prove that data originated from Amazon or is authorized for official reporting. Verify the upstream source, collection method, license, and permitted uses before making provenance claims or redistributing the dataset.

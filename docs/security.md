# 🔐 Security and Responsible Data Handling

## Project Scope

This repository contains analytical data artifacts, a PBIX report, PDF export, SQL example, and images. These files can expose information not obvious from the visible dashboard.

## Data Sensitivity

Before committing or sharing a CSV, workbook, PBIX, or PDF, determine whether it contains personal, customer, order, or commercially sensitive data. Inspect hidden worksheets, columns, model tables, hidden report pages, metadata, and source paths. Review exported pages. Do not assume a PDF is safe merely because fewer fields are visible.

## Credentials

Keep Power BI credentials, gateway passwords, SQL passwords, tokens, and connection strings out of Git. Configure authentication through approved Power BI and data-source controls. Use least privilege and rotate any credential committed accidentally.

## SQL Safety

Review SQL before execution. Use a disposable database for import and testing. Restrict permissions and avoid destructive statements unless explicitly required and backed up.

## Provenance and Rights

Verify the upstream source and permitted use of the dataset. The repository name does not prove official Amazon data provenance. Do not imply endorsement or official status without authorization. Logos, images, and fonts may have separate licensing terms.

## Reporting

Report data exposure, credential leakage, or unsafe query behavior privately to Brajesh Kumar (`@Brajesh31`). Do not attach confidential data or publish exploit details in a public issue.

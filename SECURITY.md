# 🔐 Security Policy

## Project Scope

This repository contains a Power BI report, PDF export, CSV/XLSX datasets, SQL example, and presentation assets. The main security risks involve confidential data exposure, embedded model content, credentials, unsafe SQL execution, and unauthorized redistribution.

## Reporting

Report suspected data exposure, credential leakage, or unsafe query behavior privately to Brajesh Kumar (`@Brajesh31`) through a private GitHub contact channel.

Include:
- Affected file or artifact.
- Description and potential impact.
- Reproduction steps using sanitized data.
- Relevant timestamps and screenshots with sensitive content removed.
- Suggested mitigation, if known.

Do not publish credentials, private records, or exploitable details in a public issue.

## Data Handling Requirements

- Inspect CSV/XLSX contents before committing.
- Inspect hidden worksheets, hidden columns, and named ranges.
- Review PBIX hidden tables/columns/pages, model metadata, and source settings.
- Review PDF exports before sharing.
- Remove personal machine paths and credentials.
- Share data only with an authorized audience.
- Keep private/customer/commercially sensitive exports out of Git.

## Credentials and SQL

Keep Power BI/gateway/SQL credentials and connection strings out of source control. Configure authentication via approved platform controls. Review SQL before execution and use a disposable database for experiments. Avoid destructive statements unless explicitly required and backed up.

## Third-Party Data and Branding

Verify data-source provenance and permitted redistribution. Confirm logo, trademark, image, and font terms independently. The project MIT license does not automatically override separate third-party terms.

## Coordinated Disclosure

Please allow reasonable time for investigation and remediation before public disclosure. Avoid sharing confidential evidence in public discussions.

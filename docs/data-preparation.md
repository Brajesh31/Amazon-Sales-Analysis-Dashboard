# 🧹 Data Preparation and Transformation Workflow

## 1. Preserve the Raw Source

Keep the supplied CSV and XLSX files unchanged unless a source correction is explicitly authorized and documented. Make transformations inside a clearly named Power Query layer or a separate generated output. Never overwrite raw data silently.

Record which file the PBIX actually consumes. Both CSV and XLSX are present, but they may not be interchangeable at the model level.

## 2. Profile Before Cleaning

Before changing values, record:
- row count;
- column count and exact raw headers;
- data types inferred by Power BI/Excel;
- null and blank counts per column;
- distinct count for category and shipment;
- minimum, maximum, and distribution of price values;
- minimum, maximum, and invalid count for review counts;
- earliest/latest parseable date;
- exact duplicate row count.

The baseline count stated in the repository overview is 89,082 rows and six fields. Confirm this in the actual file before treating it as a validated invariant.

## 3. Header Normalization

The source includes `Number of  reviews` with repeated spaces and a price header containing parentheses. Use stable cleaned names in the query layer, for example `number_of_reviews` and `price_usd` only once currency is verified.

Retain a mapping from raw names to transformed names. Avoid renaming the source file headers without updating all PBIX references.

## 4. Text Normalization

For category and shipment text:
- trim leading/trailing whitespace;
- remove non-printing characters only where identified;
- preserve the original raw text for audit;
- inspect case and spelling variants;
- do not merge semantically distinct values based only on appearance.

Descriptions should be retained as text. Do not truncate them without a defined business requirement.

## 5. Numeric Conversion

Price values may contain separators or currency formatting. Review the source locale first. Convert into a decimal type using an explicit culture/locale. Capture values that fail conversion.

Review counts should be converted to whole numbers after handling separators and blanks. Do not coerce invalid values to zero because that changes the meaning of missing or malformed records.

## 6. Date Conversion

Inspect a sample of `Order Date` strings and identify the source format. Convert using an explicit locale. Track conversion errors separately. Check future dates, implausible historical dates, nulls, and date ranges before using time-based analysis.

## 7. Duplicate Handling

Do not remove duplicates merely because product descriptions repeat. A repeated product can represent multiple valid records. Determine the intended row grain first. Without a stable order/product identifier, exact duplicate rows can only be flagged for investigation, not automatically assumed to be erroneous.

## 8. Output Validation

After transformation, compare:
- source and transformed row counts;
- null counts by field;
- distinct category count;
- price min/max and selected quantiles;
- review-count min/max;
- date parse failures and date range;
- duplicate candidates;
- representative source-to-output records.

Record all rows removed or quarantined and the reason for each removal.

## 9. Power Query Recommendations

Keep query steps named and ordered. Avoid embedding personal machine paths in shared files. Use descriptive staging and final query names. Disable load for intermediate queries where appropriate, but only after verifying model dependencies.

## 10. Reproducibility Record

For every released report, record source file name, file checksum if feasible, transformation/query version, Power BI Desktop version, refresh date, row counts before/after transformation, and any manually applied filters.

This repository does not currently include a standalone automated ETL script. The procedure above is a maintenance and analyst workflow, not a claim that all these transformations already exist in the PBIX.

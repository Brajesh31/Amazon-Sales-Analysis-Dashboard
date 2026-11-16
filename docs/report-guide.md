# 📊 Power BI Report User Guide

## 1. Open the Editable Report

Open `Amazon.pbix` in Microsoft Power BI Desktop. If Power BI cannot find the original data source, inspect the file/data source settings and reconnect to the correct CSV or XLSX copy.

Use a duplicate working copy before making model or report changes. The tracked PBIX is the primary editable report artifact.

## 2. PBIX Versus PDF

| PBIX | PDF |
|---|---|
| Editable report and model | Static page export |
| Can contain queries, measures, relationships, visuals | Shows only the exported state |
| Can refresh from configured sources | Cannot refresh or recalculate |
| Supports interactive filters/slicers if configured | No interactive report filtering |

A PDF may be out of date after PBIX changes. Export a new PDF after validating and saving the report.

## 3. Inspect the Report Before Interpreting It

The PBIX binary may contain report pages, visuals, data model objects, measures, and Power Query transformations. Those internals have not been fully reconstructed from plain-text repository metadata during this documentation pass.

When you open the report:
- list all report pages;
- inspect page titles and navigation;
- identify all slicers and filters;
- inspect visual titles and field wells;
- review measures and calculated columns;
- inspect relationships and filter direction;
- check hidden pages/fields;
- confirm all source queries refresh successfully.

Do not assume a particular KPI, chart, or filter exists solely because it is common in sales dashboards.

## 4. Reading Visuals Responsibly

Confirm each visual's aggregation, unit, date granularity, and filter context before interpreting it. Distinguish:
- row count from order count;
- product price from revenue;
- review count from sales volume;
- shipment description from shipment completion;
- category distribution from market share.

If a visual uses an average, verify whether it is a row-level average or a weighted business metric.

## 5. Filter and Slicer Checks

Test each slicer independently and in combination. Confirm:
- which visuals respond;
- whether selections cross-filter or highlight;
- whether a clear/reset option works;
- whether totals change as expected;
- whether filter pane selections are reflected in exported output.

## 6. Exporting PDF

After refreshing and validating the PBIX:
1. Save the report.
2. Confirm intended filters and slicers.
3. Inspect every page at readable zoom.
4. Export to PDF.
5. Review page order, truncation, labels, font rendering, and blank pages.
6. Record report refresh date and filters used.
7. Commit the refreshed PDF only if it is intended to be versioned.

## 7. Report Change Evidence

For a report modification, include before/after screenshots and summarize the affected page, visual, measure, model relationship, filter behavior, source, and validation. Binary PBIX diffs do not provide a useful human-readable review by themselves.

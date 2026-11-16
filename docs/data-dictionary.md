# 🧾 Data Dictionary

## 1. Scope

The source dataset is described as a combined product-oriented table with 89,082 rows and six columns. The fields listed below match the column names identified in the repository's project description. The CSV itself is a large binary-like text artifact and was not fully loaded through the GitHub text interface during this maintenance pass. Treat the row count and field inventory as the repository's stated metadata and confirm them against the file when preparing a production analysis.

## 2. Source Fields

| Source column | Recommended analytical type | Definition and handling |
|---|---|---|
| `Product Category` | Text / category | Category label assigned to the product record. Trim leading/trailing spaces and standardize casing carefully. |
| `Product Description` | Text | Free-form product description. Long text is not a stable product key and may repeat. |
| `Price(Dollar)` | Decimal number | Price-like value with dollar denomination indicated in the header. Parse separators/currency symbols and confirm whether all rows use the same currency and unit. |
| `Number of  reviews` | Whole number | Review-count-like field. The source name includes irregular whitespace. Rename only in a transformation layer and remove thousands separators before numeric conversion. |
| `Shipment` | Text | Shipment/destination description. The source semantics are not fully defined, so do not assume it is a normalized region, carrier, delivery state, or shipping cost. |
| `Order Date` | Date | Date-like value stored as text in the CSV. Parse using a known locale and explicitly capture failed conversions. |

## 3. Field-Level Cautions

### Product Category
Category is suitable for grouping after cleaning. Preserve the original value in the raw dataset so that standardization can be audited. Do not collapse distinct labels merely because they look similar.

### Product Description
Descriptions can be duplicated, incomplete, or written with inconsistent punctuation. Do not use description text as a primary key unless uniqueness and stability have been checked. A separate verified identifier would be preferable.

### Price(Dollar)
A product price is not sales revenue. Revenue requires a verified transaction quantity and transaction price for each order line, with returns/discounts/tax semantics defined. A product price field alone cannot calculate total sales.

Confirm:
- whether values contain currency symbols or comma separators;
- whether decimals use dot or comma;
- whether currency is consistently USD;
- whether values are list price, current price, sale price, or transaction price;
- whether null, zero, negative, or extreme values are legitimate.

### Number of  reviews
Normalize the irregular header for downstream use, for example to `NumberOfReviews`, without changing the raw source. Remove thousands separators only after confirming locale. Review count should be a whole, non-negative value unless source documentation proves otherwise.

### Shipment
The current source description calls this a shipment field, but its exact business meaning is not verified. Inspect representative values before treating it as geographic location, shipping method, fulfillment status, or delivery date. Normalize only after determining semantics.

### Order Date
The raw CSV stores this as text. Confirm date ordering and locale (for example, day/month/year versus month/day/year). Preserve unparseable raw values in a rejection/exception report rather than silently dropping them.

## 4. Recommended Transformed Names

A transformation layer may use consistent names such as:

| Raw field | Suggested cleaned field |
|---|---|
| Product Category | `product_category` |
| Product Description | `product_description` |
| Price(Dollar) | `price_usd` only after currency is confirmed |
| Number of  reviews | `number_of_reviews` |
| Shipment | `shipment_description` until meaning is verified |
| Order Date | `order_date` |

Do not label a price column `price_usd` until its currency is verified.

## 5. Missing Fields and Analytical Limits

The six documented columns do not explicitly include product ID, order ID, customer ID, quantity, revenue, profit, discount, tax, return indicator, or fulfillment timestamps. Those measures cannot be reliably derived without additional verified fields or source context.

## 6. Change Control

When the source schema changes:
1. Update this dictionary.
2. Record the raw header and cleaned field name.
3. State type conversions and locale.
4. Update Power Query/model dependencies.
5. Reconcile row counts and key aggregates.
6. Update screenshots/examples and README.

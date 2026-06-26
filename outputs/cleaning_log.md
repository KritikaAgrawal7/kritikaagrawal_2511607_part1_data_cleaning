Cleaning Log

Dataset Information

Item	Details
Input File	raw_orders.xlsx
Output File	cleaned_orders.xlsx
Project	AI Business Analytics Capstone – Part 1
Objective	Clean, validate and prepare the transactional sales dataset for downstream analytics.

⸻

1. List of Issues Found

The initial data profiling exercise identified the following data quality issues:

* Missing values in the Region, Ship Mode, and Discount columns.
* Extra internal spaces in Customer Name, Segment, Category, and Ship Mode, resulting in inconsistent text values.
* Mixed date formats and dates stored as text in the Order Date and Ship Date columns.
* Negative discount values.
* Ship dates occurring earlier than their corresponding order dates.
* Exact duplicate records.
* Duplicate Order IDs requiring business validation.
* Sales calculation mismatches.
* Profit calculation mismatches.
* Mixed display formats for discount values.

⸻

2. Cleaning Actions Performed

The following cleaning actions were carried out:

* Replaced 26 missing Region values with “Unknown”.
* Replaced 22 missing Ship Mode values with “Unknown”.
* Evaluated all 18 missing Discount values using business-rule validation:
    * 4 records were safely imputed with a discount of 0.
    * 14 records were retained as blank and flagged for review.
* Removed extra internal spaces from text fields using TRIM() and SUBSTITUTE().
* Standardized mixed date formats and converted text dates into valid Excel date values.
* Removed 20 exact duplicate records.
* Created the following calculated columns:
    * cleaned_discount
    * calculated_sales
    * calculated_profit
    * profit_margin
    * shipping_delay_days
    * order_month
    * order_year
    * data_quality_flag
* Standardized the display format of discount values while preserving their underlying numeric values.

⸻

3. Business Rules Applied

The following business rules guided the cleaning process:

* Missing Region values were replaced with “Unknown”.
* Missing Ship Mode values were replaced with “Unknown”.
* Missing Discount values were replaced with 0 only if Sales and Profit validation confirmed that imputation was appropriate.
* Missing Discount values that failed validation were retained and flagged.
* Negative discount values were retained and flagged for business review.
* Ship dates earlier than Order Dates were retained and flagged.
* Exact duplicate records were removed.
* Duplicate Order IDs were retained because they may represent legitimate business transactions.
* Original Sales and Profit values were preserved to maintain auditability.

⸻

4. Assumptions Made

The following assumptions were applied during the cleaning process:

* “Unknown” is an acceptable replacement for missing Region and Ship Mode values.
* Duplicate Order IDs may represent valid multi-line business transactions and therefore should not be removed automatically.
* Original transactional values should be preserved wherever possible.
* Derived analytical columns were created for validation and reporting without modifying the original business data.

⸻

5. Records Removed

* 20 exact duplicate records were identified and removed.
* Original dataset size: 932 records.
* Final cleaned dataset size: 912 records.

No other records were deleted during the cleaning process.

⸻

6. Records Flagged

The cleaning process retained records that required business review instead of modifying or deleting them. These records were identified using the data_quality_flag column.

Data Quality Flag	Record Count
INVALID_MISSING_DISCOUNT	14
PROFIT_MISMATCH	19
SALES_MISMATCH	18
SALES_MISMATCH + PROFIT_MISMATCH	44
SHIP_BEFORE_ORDER	18
SHIP_BEFORE_ORDER + SALES_MISMATCH + PROFIT_MISMATCH	2
INVALID_DISCOUNT + SALES_MISMATCH + PROFIT_MISMATCH	15
Total Flagged Records	130
Clean Records (OK)	782
Total Records	912

Summary

* Total records in the cleaned dataset: 912
* Clean records (OK): 782
* Records containing one or more data quality flags: 130

All flagged records were retained to preserve source data and can be identified using the data_quality_flag column.

⸻

7. Limitations of the Cleaning Process

The following limitations remain:

* The business meaning of duplicate Order IDs could not be verified using the available dataset.
* Records with invalid discount values were retained rather than corrected to preserve source data.
* Records with Sales and Profit calculation mismatches were flagged but not overwritten because the original transactional values were preserved for audit purposes.
* The cleaning process was limited to the information available in the provided dataset and associated business rules.
* 130 records continue to contain one or more data quality flags and require further business review before being used for production reporting or decision-making.

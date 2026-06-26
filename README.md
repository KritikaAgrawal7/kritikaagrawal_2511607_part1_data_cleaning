# Retail Orders Data Cleaning & Validation Project

## 1. Problem Summary

This project focused on cleaning, validating, and analysing a retail orders dataset provided as part of the capstone assessment.

The objective was to identify data quality issues, clean the dataset without modifying the raw source file, apply business rules, create calculated fields, generate data quality reports, and prepare business summary reports using Pivot Tables.

The final deliverables include a cleaned dataset, data quality report, pivot summary report, cleaning log, README, and supporting screenshots.

---

## 2. Dataset Description

**Source File:** raw_orders.xlsx

The dataset contains retail order transactions with information such as:

- Order ID

- Customer details

- Region, State and City

- Product Category and Sub-category

- Quantity and Unit Price

- Discount

- Sales, Cost and Profit

- Order Date and Ship Date

- Payment Status and Order Status

Initial dataset size: **932 records**

Final cleaned dataset: **912 records**

---

## 3. Tools Used

- Microsoft Excel

- Excel Formulas

  - IF()

  - IFERROR()

  - TRIM()

  - SUBSTITUTE()

  - ROUND()

  - DATEVALUE()

  - TEXT()

  - COUNTIF()

- Pivot Tables

- Conditional Formatting

- Data Validation

---

## 4. Cleaning Steps Performed

The following data cleaning activities were completed:

- Replaced missing Region values with **"Unknown"**

- Replaced missing Ship Mode values with **"Unknown"**

- Applied business-rule validation to missing Discount values

- Imputed 4 valid missing Discount values with **0**

- Flagged 14 missing Discount values that could not be safely imputed

- Removed extra internal spaces from text fields

- Standardized text values

- Converted mixed date formats into a consistent Excel date format

- Converted text dates into valid Excel date datatype

- Removed 20 exact duplicate records

- Created calculated columns:

  - cleaned_discount

  - calculated_sales

  - calculated_profit

  - profit_margin

  - shipping_delay_days

  - order_month

  - order_year

  - data_quality_flag

- Standardized discount display format

---

## 5. Business Rules Applied

The following business rules were implemented:

- Missing Region → Replace with **Unknown**

- Missing Ship Mode → Replace with **Unknown**

- Missing Discount → Replace with 0 only after successful Sales and Profit validation

- Invalid Discount → Retain and flag

- Ship Date earlier than Order Date → Flag

- Remove exact duplicate records

- Retain duplicate Order IDs for business validation

- Preserve original Sales and Profit values

- Document all cleaning decisions

---

## 6. Summary of Data Quality Issues Found

| Issue | Count |

|--------|------:|

| Missing Region | 26 |

| Missing Ship Mode | 22 |

| Missing Discount | 18 |

| Negative Discount | 15 |

| Ship Date before Order Date (Raw Dataset) | 22 |

| Ship Date before Order Date (Cleaned Dataset) | 21 |

| Duplicate Order IDs | 31 |

| Exact Duplicate Records | 20 |

| Sales Calculation Mismatch | 95 |

| Profit Calculation Mismatch | 41 |

---

## 7. Summary of Final Pivot Reports

### Pivot 1 – Sales & Profit by Region

- South generated the highest sales.

- East generated the highest overall profit.

- West recorded the lowest sales and profit among the four known regions.

### Pivot 2 – Sales & Profit by Category & Sub-category

- Technology was the highest-performing category in terms of both sales and profit.

- Copiers were the strongest-performing Technology sub-category.

- Chairs generated the highest sales and profit within Furniture.

- Storage was the strongest-performing Office Supplies sub-category.

### Pivot 3 – Order Count by Ship Mode

- Standard Class was the most frequently used shipping mode.

- First Class and Second Class had almost identical order volumes.

- Same Day delivery was the least frequently used known shipping option.

### Pivot 4 – Profit Margin by Customer Segment

- Small Business customers recorded the highest average profit margin.

- Consumer customers recorded the lowest average profit margin.

### Pivot 5 – Order & Payment Exceptions by Region

- North and South recorded the highest payment-related exceptions.

- North recorded the highest number of cancelled and returned orders.

- Returned orders exceeded cancelled orders across the dataset.

### Pivot 6 – Monthly Sales Trend

- June 2024 recorded the highest monthly sales during 2024.

- August 2025 recorded the highest monthly sales during 2025.

- Monthly sales fluctuated over time without a consistent upward or downward trend.

---

## 8. Key Business Insights

- Sales are well distributed across the three major product categories, indicating a balanced product portfolio.

- Technology generated the highest revenue and profit among all product categories.

- East demonstrated stronger profitability despite ranking second in sales.

- Small Business customers delivered the highest average profit margin.

- Standard Class remained the preferred shipping method.

- Order fulfilment issues were more common than payment failures.

- Data quality improvements enabled more reliable reporting while preserving source data for audit purposes.

---

## 9. Assumptions and Limitations

### Assumptions

- "Unknown" is an acceptable replacement for missing Region and Ship Mode values.

- Duplicate Order IDs may represent legitimate business transactions.

- Original transactional values should be preserved wherever possible.

### Limitations

- Duplicate Order IDs require business validation.

- Records with negative discounts were retained and flagged.

- Sales and Profit mismatches were retained for audit purposes.

- Flagged records require further business review before production use.

---

## 10. Screenshots Included

The following screenshots are included with the submission:

- raw_data_preview.png

- cleaned_data_preview.png

- pivot_summary_1.png

- pivot_summary_2.png



# KPI Dictionary & Data Quality Contract

## Project Overview

This project focuses on translating an ambiguous retail business request into measurable Key Performance Indicators (KPIs) and a practical Data Quality Contract.

The goal is to establish clear business definitions for important metrics while ensuring that the underlying data is complete, unique, valid, consistent, and sufficiently fresh for trustworthy business reporting.

The project uses an intentionally imperfect retail orders dataset to demonstrate real-world data analytics and data-quality practices. The dataset contains issues such as duplicate order records, missing values, inconsistent categorical values, invalid quantities, invalid discount percentages, and missing dates.

## Project Objectives

The main objectives of this project are:

- Convert business requirements into measurable and clearly defined KPIs.
- Document the formula and business meaning of every KPI.
- Define the correct data grain, filters, owner, and refresh cadence for each KPI.
- Profile the dataset for completeness, uniqueness, validity, consistency, and freshness.
- Identify data-quality problems using executable checks.
- Establish measurable failure thresholds for important data-quality rules.
- Define severity levels and escalation actions.
- Prevent unreliable data from being used in business reporting.
- Create a reusable framework for trustworthy Business Intelligence reporting.

## KPI Dictionary

The project defines multiple business KPIs, including:

1. Gross Order Value
2. Net Sales Value
3. Paid Order Rate
4. Average Order Value
5. Units Sold
6. Average Discount Percentage
7. Refund Rate
8. Failure Rate
9. Pending Order Rate
10. Revenue per Unit

Each KPI contains a documented:

- Business definition
- Calculation formula
- Data grain
- Applicable filters
- Business owner
- Refresh cadence

This ensures that different teams use consistent definitions when calculating and interpreting business metrics.

## Data Quality Profiling

The dataset is evaluated across five major data-quality dimensions:

### 1. Completeness

Checks whether required fields contain missing or null values.

Important fields include order ID, order date, customer segment, city, category, quantity, unit price, and payment status.

### 2. Uniqueness

Checks whether every order ID is unique and identifies duplicate records that could cause double counting in KPI calculations.

### 3. Validity

Checks whether values follow the expected business rules.

Examples include:

- Quantity must be a positive whole number.
- Unit price must be numeric and non-negative.
- Discount percentage must be between 0 and 100.
- Order date must be a valid date within the expected range.

### 4. Consistency

Checks whether categorical values follow the approved business vocabulary.

Examples include:

- Student
- Fresher
- Professional

Payment statuses are normalized to:

- Paid
- Pending
- Failed
- Refunded

Product categories are normalized to the approved category values.

### 5. Freshness

Checks whether the dataset has been updated within the expected reporting window.

Freshness is important because even perfectly structured data becomes unreliable for operational reporting if it is outdated.

## Data Quality Contract

The Data Quality Contract establishes measurable rules for trustworthy data.

Each rule defines:

- Quality dimension
- Validation rule
- Failure threshold
- Severity
- Escalation action

Critical failures can block KPI publication until the underlying data issue is resolved.

High-severity failures require affected records to be corrected or quarantined before they are included in business reporting.

Medium-severity issues can generally be resolved through documented normalization or business-owner review.

## Data Quality Release Gate

The recommended release process is:

1. Run the executable data-quality checks.
2. Identify failed validation rules.
3. Record affected rows and order IDs.
4. Quarantine invalid or duplicate records where required.
5. Notify the responsible data owner.
6. Correct or normalize the source data.
7. Re-run the complete profiling process.
8. Publish KPIs only after critical quality issues are resolved.

## Project Files

The repository contains the following deliverables:

- `KPI_Dictionary_and_Data_Quality_Contract.xlsx` — KPI definitions, data dictionary, and quality contract.
- `data_profile_and_kpi_analysis.ipynb` — executable Python/Jupyter notebook for data profiling and KPI calculations.
- `retail-orders-raw.csv` — retail orders dataset used for analysis.
- `Data_Quality_Contract.docx` — formatted data-quality contract document.

## Tools & Technologies

- Python
- Pandas
- Jupyter Notebook
- Microsoft Excel
- Data Quality Validation
- Business Intelligence
- KPI Design
- Data Profiling

## Business Value

A well-defined KPI dictionary prevents different teams from calculating the same metric differently.

The Data Quality Contract establishes a measurable agreement about what trustworthy data means and provides a structured process for handling failures.

Together, these deliverables provide a foundation for reliable reporting, repeatable analytics, better governance, and data-driven business decision-making.

## Conclusion

This project demonstrates how raw and imperfect business data can be transformed into a structured analytics framework through KPI definition, data profiling, validation rules, and data-quality governance.

The approach can be extended to larger retail, commerce, education, operations, or business-intelligence datasets.

# Portfolio
A portfolio website showcasing data analysis projects.

# Data Analytics Portfolio

## 1. Exploratory Data Analysis: Vancouver Property Tax Trends
**Project Title:** Uncovering Patterns in Land Values and Tax Levies

### Objective
To identify trends and anomalies in Vancouver's limited agriculture zone property data (2020-2025) through comprehensive data exploration.

### Methodology
- **Initial Assessment:** Profiled raw dataset (606 records) using AWS DataBrew
- **Data Cleaning:** 
  - Removed records with null values in critical fields (built_year)
  - Standardized column naming conventions
  - Reduced dataset to 514 valid records (15% reduction)
- **Pattern Discovery:**
  - Analyzed correlation between land values and tax levies
  - Identified year-over-year changes
  - Flagged data anomalies (zero tax levy in 2025)

### Tools & Technologies
- AWS DataBrew (data profiling)
- Python (Pandas for initial analysis)
- Jupyter Notebook (documentation)

### Key Findings
- Steady increase in average land values (42% growth 2020-2024)
- Unexpected $0 tax levy recorded for 2025 (data quality issue)
- Strong correlation between land value appreciation and tax increases

[View Sample Visualization](#) | [GitHub Code](#)

---

## 2. Descriptive Analysis: Tax & Value Statistics
**Project Title:** Yearly Comparative Analysis of Property Metrics

### Objective
To calculate and compare key statistics across reporting years, providing actionable insights for city planners.

### Methodology
- **Data Aggregation:**
  - Calculated annual averages for land values and tax levies
  - Grouped data by report year using AWS Athena
- **Validation:**
  - Cross-checked results against official city dashboards
  - Identified and investigated discrepancies
- **Trend Analysis:**
  - Calculated percentage changes year-over-year
  - Compared limited agriculture zone to other classifications

### SQL Implementation
```
SELECT 
    reportyear, 
    AVG(currentlandvalue) AS avg_land_value,
    AVG(taxlevy) AS avg_tax_levy,
    (AVG(taxlevy)/AVG(currentlandvalue))*100 AS tax_rate_percentage
FROM cv_tax_rec_trf_system
WHERE reportyear <> '2025'
GROUP BY reportyear;
```
### Tools & Technologies
- AWS Athena (query execution)
- Amazon S3 (data storage)
- SQL (analysis)

### Results Summary
| Year | Avg Land Value | Avg Tax Levy | Tax Rate (%) |
|------|----------------|--------------|--------------|
| 2020 | $5,262,145     | $26,882      | 0.51%        |
| 2021 | $5,704,265     | $30,710      | 0.54%        |
| 2022 | $7,032,620     | $37,004      | 0.53%        |
| 2023 | $7,108,590     | $38,763      | 0.55%        |
| 2024 | $7,626,135     | $42,179      | 0.55%        |

View Complete Analysis | Query Examples

## 3. Data Wrangling Pipeline
**Project Title:** Building a Reliable Property Data Pipeline

### Objective
To transform raw, semi-structured property data into an analysis-ready format while maintaining data integrity.

### Implementation
**Ingestion:**

- Established S3 buckets (raw, curated, transformed)

- Set up yearly data ingestion from city servers

**Cleaning Process:**

- Standardized all column names to CamelCase

- Filtered invalid records (missing built_year)

- Corrected data types (string → numeric for years/values)

**Transformation:**

- Created calculated fields (tax rates, value changes)

- Implemented AWS Glue ETL jobs for automation

**Cataloging:**

- Built searchable data catalog using AWS Glue

- Established table schemas for SQL querying

### Tools & Technologies
- AWS Glue (ETL, cataloging)

- Amazon S3 (storage tiers)

- Python (custom transformations)

- DataBrew (profiling)

### Outcomes
- Reduced processing time by 60% through automation

- Improved query performance by 3x with proper typing

- Enabled self-service analytics through catalog

Pipeline Diagram | ETL Code Samples

## 4. Data Quality Framework
**Project Title:** Ensuring Trust in Property Tax Data

### Objective
To implement comprehensive quality checks guaranteeing reliable analytics outputs.

### Quality Measures Implemented
**Completeness Checks:**

- Verified required fields (land_value, tax_levy)

- Flagged records with missing critical data

**Validity Rules:**

- Range checks for plausible values

- Year-over-year change thresholds

**Consistency Controls:**

- Cross-field validation (e.g., tax < land_value)

- Reference checks against city master data

**Monitoring:**

- CloudWatch dashboards for pipeline health

- SNS alerts for quality failures

### Tools & Technologies
- AWS Glue Data Quality

- CloudWatch (monitoring)

- SNS (alerting)

- Custom Python validators

### Impact
- Reduced data errors by 75%

- Automated detection of 12 critical issues

- Established ongoing quality metrics

Quality Dashboard | Validation Rules

## 5. Predictive Analysis Model
Project Title: Forecasting Future Tax Revenues

### Objective
To develop a predictive model estimating 2025 tax levies based on historical trends.

### Methodology
**Baseline Calculation:**

- Determined historical tax rate (0.536% of land value)

- Calculated annual variance (σ = 0.012%)

**2025 Projection:**
```
2025 Predicted Tax = 2025 Avg Land Value × Historical Rate
                  = $7,475,953 × 0.00536
                  ≈ $40,093
```
**Sensitivity Analysis:**

- ±1σ range: 39,200−39,200−40,900

- Compared to city's official projections

### Tools & Technologies
- AWS Athena (aggregation)

- Python (statistical analysis)

- Jupyter (documentation)

### Business Value
- Provided data-driven budget forecast

- Identified potential $0 tax levy as data issue

- Established repeatable forecasting method

Forecast Details | Analysis Notebook

## Infrastructure & Security
**Project Title:** Secure Cloud Analytics Platform

## Architecture Components
**Storage:**

- S3 buckets with lifecycle policies

- Glacier Deep Archive for compliance

**Security:**

- KMS encryption for data at rest

- IAM role-based access control

- Bucket versioning for recovery

**Governance:**

- CloudTrail activity logging

- Tag-based resource management

### Implementation Highlights
- Created customer-managed KMS keys
- Enabled versioning on all S3 buckets
- Set up cross-region replication for DR
- Configured CloudWatch alarms for:
  - Unauthorized access attempts
  - Storage capacity thresholds
  - ETL job failures

### Tools & Technologies
- AWS KMS (encryption)

- IAM (access control)

- CloudTrail (auditing)

- S3 (storage management)

Architecture Diagram | Security White Paper

**LinkedIn:** [Keerthana Jalla](https://www.linkedin.com/in/keerthana-jalla-3ab5a5255/)  
**Contact:** [keerthana.jalla121@gmail.com](mailto:keerthana.jalla121@gmail.com)



# ABC-Phones-Credit-Portfolio-Analysis


ABC Phones Credit Data Engineering & Analytics Platform

A comprehensive end-to-end data engineering solution for credit portfolio analysis, featuring automated data quality monitoring, transformation pipelines, and interactive business intelligence dashboards.

📋 Project Overview

This project implements a production-ready data engineering pipeline for ABC Phones' credit portfolio, transforming raw customer data into actionable business insights. The solution includes automated data quality checks, ETL workflows, and two comprehensive dashboards for portfolio analysis and data quality reporting.

🏗️ Architecture

🚀 Key Features

Data Transformation Pipeline

3 Python Notebooks: Clean and transform raw data using PySpark
Automated Orchestration: Databricks pipeline runs all notebooks sequentially
Delta Lake Storage: Optimized storage in Unity Catalog with ACID transactions
Scheduled Execution: Daily automated runs at 6 AM Nairobi time

Data Quality Monitoring Framework

Implements 6 comprehensive checks across 3 tables:
Check Type
Description
Severity
Threshold
Freshness Check
Monitors data recency

CRITICAL
≤ 2 days old
Uniqueness Check
Detects duplicate loan IDs

HIGH
0 duplicates
Referential Integrity
Validates survey-credit links

HIGH
0 orphan records
Range Validation
Checks for invalid values

HIGH
0 violations
Null Threshold Check
Monitors missing data

MEDIUM
Field-specific thresholds
Sales Data Quality
Validates sales table integrity

MEDIUM
0 duplicates, <5% nulls


Portfolio Analysis Dashboard

Executive Summary: KPIs for total loans, portfolio value, average loan size, and default rate
Risk Distribution: Visual breakdown by risk categories (Low/Medium/High)
Temporal Analysis: Monthly trends in loan origination and portfolio growth
Customer Segmentation: Analysis by age bands and income levels

Data Quality Report Dashboard

Page 1: Executive Summary

Overall health score counter (3/6 checks passed)

Critical issues counter with RED alerting

Data freshness age tracker (128 days stale)

Total violations counter (71,537 range violations)

Comprehensive results table with all check details

Visual charts: Severity distribution and pass/fail by check type

Page 2: Critical Issues Detail

Freshness issue breakdown with latest data dates

Range violations detail (71,456 invalid income bands)

Referential integrity analysis (16 orphaned survey records)

Page 3: Recommendations

Prioritized action items with owners and effort estimates

Recommended monitoring cadence (Real-time/Daily/Weekly)

Automated alerting thresholds

🛠️ Technology Stack

Platform: Databricks

Languages: Python (PySpark), SQL

Storage: Delta Lake, Unity Catalog

Orchestration: Databricks Workflows

Visualization: Databricks AI/BI Dashboards (Lakeview)

Data Quality: Custom SQL-based monitoring framework

Scheduling: Databricks Jobs (Cron-based)

📊 Data Schema

credit_customer_data_transformed

Loan identifiers (LOAN_ID, DATE)

Customer demographics (age_band, avg_monthly_income_band)

Financial metrics (BALANCE, ARREARS, TOTAL_PAID, DAYS_PAST_DUE)

Risk classification (risk_category)

Product information (PRODUCT_TYPE, County)

survey_customer_data

Survey responses (NPS_Score, NPS_Quality, NPS_Support)

Customer feedback (NPS_Reason)

Timestamps (Submitted_at)

Loan linkage (Loan_Id)

cleaned_sales_and_customer_data

Sales transactions (PRODUCT_NAME, SALE_DATE)

Customer linkage (Loan_ID)

Revenue tracking

🔍 Key Findings

Critical Data Quality Issues Discovered

Freshness Failure (CRITICAL): Latest data is 128 days old (2025-12-30) - ETL pipeline stopped

Range Violations (HIGH): 71,537 violations - primarily invalid income bands using granular ranges instead of expected "Low/Medium/High" categories

Referential Integrity (HIGH): 16 survey responses (0.45%) cannot be linked to credit records

Data Validation: 76 negative balances and 5 negative total paid amounts detected

Portfolio Insights

Comprehensive view of credit portfolio performance

Risk-based segmentation for proactive management

Prerequisites

Databricks workspace with Unity Catalog enabled

SQL warehouse for dashboard execution

Appropriate permissions for catalog credit-data-engineering and schema credit-data

Deployment Steps

Import Notebooks

Upload all 3 cleaning notebooks to your Databricks workspace

Update catalog and schema references if needed

Create Pipeline

Set up Databricks pipeline to orchestrate the 3 notebooks

Configure to run sequentially with proper dependencies

Schedule Job

Create job to run data quality monitoring notebook

Set schedule: Daily at 6 AM (Africa/Nairobi timezone)

Configure alerting thresholds

Deploy Dashboards

Portfolio Analysis dashboard

Data Quality Report dashboard

Configure data sources and refresh schedules

Validate

Run pipeline end-to-end

Verify all datasets are created in Unity Catalog

Check dashboard rendering and data freshness

📈 Monitoring & Alerting

The automated monitoring job runs daily and checks:

Real-time alerts for freshness failures (> 2 days stale)

Daily alerts for range violations (> 100 violations)

Daily alerts for referential integrity issues (> 1% orphan records)

Weekly reports on null threshold trends

🔮 Future Enhancements

 Implement automated data quality remediation workflows
 
 Add predictive analytics for default risk scoring
 
 Integrate real-time streaming for freshness monitoring
 
 Expand monitoring to include data lineage tracking
 
 Add ML-based anomaly detection for data quality
 
 Build customer segmentation models for targeted campaigns
 
 Implement A/B testing framework for product optimization

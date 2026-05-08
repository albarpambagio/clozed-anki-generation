---
name: ecommerce-analytics-workflow
description: Execute end-to-end e-commerce data analysis from raw CSV to dashboard-ready insights. Use when working with transactional data, order datasets, customer data, or any e-commerce analytics project involving PostgreSQL, Python ETL, and Power BI dashboards.
---

# E-Commerce Analytics Workflow

End-to-end workflow for analyzing transactional e-commerce data. Load, clean, model, analyze, and present.

## Workflow Overview

```
Task Progress:
- [ ] Phase 1: Setup — Database, Python env, data download
- [ ] Phase 2: Clean & EDA — Data quality, profiling, issue log
- [ ] Phase 3: Model — Star schema, fact + dimension tables
- [ ] Phase 4: KPIs — Metric definitions, formula-based views
- [ ] Phase 5: Analyze — Insights, trends, segments
- [ ] Phase 6: Present — Dashboard, narrative, recommendations
```

## Phase 1: Setup

### Database

- Use PostgreSQL locally (port 5433)
- Create database, create tables from CSV schemas
- Use Python scripts for ETL (not raw SQL) for better error handling

### Project Structure

```
project/
├── data/         # CSV files (gitignored if large)
├── sql/          # SQL and Python scripts
├── logs/         # Analysis and quality logs
├── docs/         # Dashboards, guides, frameworks
└── README.md     # Stakeholder-facing report
```

## Phase 2: Clean & EDA

### Data Quality Framework

1. **Check grain**: Verify each row's meaning (1 row = 1 order, 1 transaction, etc.)
2. **Check nulls**: Identify columns with missing data. Decide: drop, impute, or flag
3. **Check duplicates**: Look for duplicate rows in key columns. Deduplicate if needed
4. **Check types**: Ensure dates are dates, numbers are numbers, IDs are strings
5. **Check ranges**: Look for outliers (negative prices, future dates, etc.)

### Issue Log

Document all findings in `logs/phase2_cleaning_eda.log.md`:

```markdown
| Issue | Impact | Resolution |
|-------|--------|------------|
| [Describe issue] | [Business impact] | [How it was fixed] |
```

## Phase 3: Model (Star Schema)

Design a star schema optimized for analytics:
- **Fact table**: Measures (revenue, quantity, scores) + foreign keys to dimensions
- **Dimension tables**: Entities (time, product, customer, location) — one row per entity

See [star-schema-design](../star-schema-design/SKILL.md) for detailed patterns.

## Phase 4: KPIs

Define KPIs as SQL views. Each KPI needs:
- **Formula**: Precise calculation
- **Business meaning**: Why this metric matters
- **Dimensions**: How to slice (by time, category, region)

### Common E-Commerce KPIs

| KPI | Formula | Dimensions |
|-----|---------|------------|
| Revenue | SUM(price * quantity) | Time, category, region |
| AOV | Revenue / Orders | Time, region |
| Repeat Rate | Repeat Customers / Total Customers | Time |
| Conversion Rate | Completed / Started | Channel, time |

## Phase 5: Analyze

### Insight Categories

Organize findings into three types:

1. **Market context** — Background that explains "why" but isn't directly actionable
2. **Further investigation** — Observations needing more data
3. **Actionable recommendations** — Specific, targeted, with expected impact

### Recommendation Template

```markdown
#### [Title] ([Priority])

**Target:** [Who or what this addresses]

**Actions:**
- [Specific action 1]
- [Specific action 2]

**Expected Impact:**
- [Quantified outcome]
```

## Phase 6: Present

Structure the README as a stakeholder report:

1. **Background & Overview** — Project summary, dataset, tech stack
2. **Data Structure** — Schema model, pipeline diagram
3. **Executive Summary** — Key metrics at a glance
4. **Insights Deep Dive** — Findings organized by theme
5. **Recommendations** — Actionable business suggestions

## Verification

Before considering the analysis complete:

- [ ] All SQL scripts run without errors
- [ ] KPIs match across views and reports
- [ ] Number of orders/transactions reconciles with source data
- [ ] README tells a story from business question to recommendations
- [ ] Data quality issues are documented in logs
- [ ] Star schema is documented with diagram

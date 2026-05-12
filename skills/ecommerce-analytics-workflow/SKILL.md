---
name: ecommerce-analytics-workflow
description: Execute end-to-end e-commerce data analysis from raw CSV to dashboard-ready insights. Use when working with transactional data, order datasets, customer data, or any e-commerce analytics project involving PostgreSQL, Python ETL, and Power BI dashboards.
---

# E-Commerce Analytics Workflow

End-to-end workflow for analyzing transactional e-commerce data. This is a domain-specific specialization of `data-analytics-workflow`. Each phase delegates to a dedicated skill for detailed patterns.

## Pipeline Overview

```
[1] Setup → [2] Clean & EDA → [3] Model → [4] KPIs → [5] Analyze → [6] Present
```

## Phase 1: Setup

- Use PostgreSQL locally. Create database, create tables from CSV schemas
- Use Python for ETL (better error handling than raw SQL)
- Name scripts sequentially: `01_create_tables.sql`, `load_data.py`, etc.

See [data-pipeline-automation](../data-pipeline-automation/SKILL.md) for ETL patterns, connection config, and logging templates.

## Phase 2: Clean & EDA

Apply CLEAN framework to e-commerce data:

| Check | What to Look For |
|-------|-----------------|
| Grain | 1 row = 1 order item? 1 transaction? |
| Nulls | Missing delivery dates, NULL review scores |
| Duplicates | Repeated order IDs, repeated zip codes in geolocation |
| Types | Dates stored as strings? Prices stored as text? |
| Ranges | Negative prices, future ship dates, 200-day delivery outliers |

Document issues in `logs/phase2_cleaning_eda.log.md`.

See [data-quality-assessment](../data-quality-assessment/SKILL.md) for the full CLEAN framework and issue log template.

## Phase 3: Model (Star Schema)

Design a star schema for e-commerce:

- **Fact table**: `fact_orders` (revenue, freight, review_score, is_late, is_repeat)
- **Dimensions**: `dim_date`, `dim_customer`, `dim_product`, `dim_seller`

See [star-schema-design](../star-schema-design/SKILL.md) for patterns and anti-patterns.

## Phase 4: KPIs

Define KPI views with formula + business meaning:

| KPI | Formula | Dimensions |
|-----|---------|------------|
| Revenue | SUM(price) | Time, category, region |
| AOV | Revenue / Orders | Time, region |
| Repeat Rate | Repeat Customers / Total | Time |
| Conversion Rate | Completed / Started | Channel, time |

## Phase 5: Analyze

Organize findings using SCAN framework:

See [analytics-insight-generation](../analytics-insight-generation/SKILL.md) for the SCAN framework and recommendation template.
See [analytics-deep-dive](../analytics-deep-dive/SKILL.md) for North Star decomposition and cross-tab methodology.

## Phase 6: Present

Structure the README as a stakeholder report:

1. **Background & Overview** — Project summary, dataset, tech stack
2. **Data Structure** — ER diagram, pipeline, quality notes
3. **Executive Summary** — Key metrics at a glance
4. **Insights Deep Dive** — Findings organized by theme
5. **Recommendations** — Actionable business suggestions

See [dash-dashboard-framework](../dash-dashboard-framework/SKILL.md) for dashboard design.
See [portfolio-dashboard-build](../portfolio-dashboard-build/SKILL.md) for portfolio presentation standards.

## Verification

- [ ] All scripts run end-to-end without errors
- [ ] KPIs match across views and reports
- [ ] Order count reconciles with source data
- [ ] README tells a story from business question to recommendations
- [ ] Data quality issues documented in logs

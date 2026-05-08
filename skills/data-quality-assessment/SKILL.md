---
name: data-quality-assessment
description: Assess and document data quality using the CLEAN framework. Use when working with new datasets, profiling raw data, identifying issues, and documenting remediation steps for analytics projects.
---

# Data Quality Assessment

Assess data quality systematically using the CLEAN framework.

## CLEAN Framework

### C — Conceptualize

Understand the data before analyzing:
- **Grain**: What does one row represent? (1 order, 1 customer, 1 transaction)
- **Metrics**: Which columns are measures vs. dimensions?
- **Relationships**: How do tables connect? (foreign keys, joins)
- **Scope**: What time period, geography, or segment does the data cover?

### L — Locate

Find solvable issues:

| Issue | How to Detect | Severity |
|-------|---------------|----------|
| Missing values | `IS NULL` checks | Medium |
| Duplicates | `COUNT(DISTINCT) vs COUNT(*)` | High |
| Type mismatches | Check date/number columns parse | High |
| Outliers | Statistical range checks | Medium |
| Foreign key orphans | LEFT JOIN WHERE NULL | High |
| Logic errors | Cross-field validation (price × qty ≠ total) | High |

### E — Evaluate

Document issues that can't be fixed:
- Data source limitations (missing fields, short time range)
- Known biases or gaps
- Assumptions made during analysis
- Impact on conclusions

### A — Augment

Add calculated fields to enrich data:

| Augmentation | Example | Purpose |
|-------------|---------|---------|
| Boolean flags | `is_late`, `is_repeat_customer` | Classification |
| Derived metrics | `days_to_delivery`, `freight_pct` | Normalization |
| Segmentation | RFM scores, customer tiers | Behavior grouping |
| Translations | Category name mapping | Localization |

### N — Note

Log everything in a structured file (`logs/phase2_cleaning_eda.log.md`):

```markdown
# Data Quality Log - [Dataset Name]

## Issues Found

| Issue | Table | Rows Affected | Severity | Resolution |
|-------|-------|---------------|----------|------------|
| Missing category names | products | 15 | Low | COALESCE to 'unknown' |
| Duplicate geolocation | geo | 3,021 | Medium | Created deduped view |

## Assumptions
- Orders > 60 days delivery flagged as anomalies (0.3% of data)
- Missing review scores excluded from average (not imputed)

## Unresolvable Issues
- Marketing data only covers 2017-2018 (e-commerce has 2016-2018)
- No carrier identifier available for logistics analysis
```

## Quality Log Template

```markdown
| Issue | Impact | Resolution |
|-------|--------|------------|
| [What was wrong] | [Business consequence] | [How it was fixed/noted] |
```

## Verification

After cleanup:
- [ ] Key metrics recalculate correctly
- [ ] Grain is consistent (no accidental double-counting)
- [ ] All assumptions documented
- [ ] Unfixable issues flagged in conclusions

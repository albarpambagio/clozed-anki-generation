---
name: project-scaffolding
description: Evaluate and scope analytics projects using the READY framework — Representative data, Exec-driven questions, Analytical frameworks, Data best practices, Your insights. Use when starting a new portfolio project, selecting datasets, or defining project scope and stakeholder questions.
---

# Project Scaffolding

Assess project readiness using the READY framework. Ensures the project is job-portfolio quality before a single line of code is written.

## Quick Start

```markdown
Dataset selected:    [name, source, rows, date range]
Exec question:       [should Team X do Y based on metric Z?]
North Star metric:   [primary KPI]
North Star dims:     [top 2-3 slicing dimensions]
Deliverable:         [dashboard / report / brief, for whom, by when]
```

## READY Framework

### R — Representative Data

Data must look like real job data — messy enough to demonstrate cleaning, large enough to require structured analysis.

| Criteria | Must-Have | Nice-to-Have |
|----------|-----------|--------------|
| Volume | 50,000+ rows | 100,000+ rows |
| Dimensions | Time + 2-3 categorical slices | Multiple granularities |
| Messiness | Nulls, duplicates, inconsistencies | Join tables with mismatches |
| Source | Public dataset (Kaggle, gov) | Network source or volunteer engagement |

### E — Exec-Driven Questions

Define 1-3 questions a VP or Head-of-something would ask. Use this pattern:

> *"Should [stakeholder role] [decision] based on [metric/dimension]?"*

Examples:
- *"Should the VP of Marketing reallocate budget from Organic to Paid Search based on LTV/MQL?"*
- *"Should the Head of Product discontinue the accessories line given its declining revenue share?"*

Test each question: **Who gets fired if this isn't answered?**

### A — Analytical Frameworks

| Phase | Framework | Output |
|-------|-----------|--------|
| Data Cleaning | CLEAN (`data-quality-assessment`) | Issues log |
| Exploratory Analysis | SCAN (`analytics-insight-generation`) | Insights log |
| Deep Dive | North Star decomposition + cross-tab (`analytics-deep-dive`) | Quantified root causes |
| Dashboard Design | DASH (`dash-dashboard-framework`) | Wireframes & page guide |

### D — Data Best Practices

- Use SQL for querying, Python for ETL, a dashboard tool for presentation
- Name phase scripts sequentially: `phase1_`, `phase2_`, etc.
- Log all decisions with rationale
- Never delete raw data — derive cleaned copies

### Y — Your Insights & Impact

Every finding must pass the "so what?" test:
- **Contextual**: Explains why something happened
- **Directional**: Points to something worth investigating
- **Actionable**: Has a clear next step with quantified impact

## Verification

- [ ] Dataset has 50,000+ rows and 2+ dimensions
- [ ] Exec questions map to a named stakeholder with budget authority
- [ ] Each planned framework produces a named deliverable
- [ ] One-sentence project summary passes the "so what?" test

---
name: data-analytics-workflow
description: Execute end-to-end data analysis from raw data to dashboard-ready insights across any industry. Use when starting a new analytics project involving data cleaning, modeling, KPI definition, and stakeholder presentation — regardless of domain.
---

# Data Analytics Workflow

Industry-agnostic end-to-end pipeline. Adapt to any domain (e-commerce, healthcare, SaaS, finance) by swapping domain-specific metrics and dimensions.

## Pipeline Overview

```
[1] Scope → [2] Clean → [3] Model → [4] KPIs → [5] Analyze → [6] Present
```

## Phase 1: Scope

Define the project before touching data:

| Element | Question to Answer |
|---------|-------------------|
| Stakeholder | Who is the decision-maker with budget authority? |
| Decision | What will they do differently after seeing this? |
| Metric | What is the primary KPI (North Star)? |
| Dimensions | What categories will you slice by? |
| Time period | What date range is relevant? |

See [project-scaffolding](../project-scaffolding/SKILL.md) for the full READY framework.

## Phase 2: Clean & EDA

Apply the CLEAN framework systematically:

| CLEAN Step | What to Do | Output |
|------------|-----------|--------|
| Conceptualize | Document grain, metrics, dimensions | Grain statement |
| Locate | Identify nulls, duplicates, type issues | Issues log |
| Evaluate | Flag unsolvable issues with impact % | Unfixable items list |
| Augment | Derive time grains, calculated fields | New columns |
| Note | Document all decisions in log | `phase2_cleaning_eda.log.md` |

See [data-quality-assessment](../data-quality-assessment/SKILL.md) for detailed CLEAN patterns.

## Phase 3: Model (Star Schema)

Design a star schema: one fact table (measures + FKs) surrounded by dimension tables (entities).

| Element | Example |
|---------|---------|
| Fact | orders (revenue, quantity, dates) |
| Dimensions | time, product, customer, location |

See [star-schema-design](../star-schema-design/SKILL.md) for patterns and anti-patterns.

## Phase 4: KPIs

Define KPIs as SQL views with formula + business meaning. Each KPI should answer a stakeholder question directly.

| KPI Type | Formula | Stakeholder |
|----------|---------|-------------|
| Revenue | SUM(price × quantity) | Finance, execs |
| Conversion | Completed / Started | Marketing, sales |
| Retention | Returning / Total | Product, growth |
| Efficiency | Output / Input | Operations |

## Phase 5: Analyze

Organize findings by type:

| Type | Definition | Example |
|------|-----------|---------|
| Contextual | Explains "why" but not directly actionable | Macroeconomic trend |
| Directional | Points to something worth investigating | Anomalous segment |
| Actionable | Clear next step with quantified impact | Reallocate budget |

### Deeper Discovery

If a finding needs root-cause investigation:

1. **Decompose** the North Star metric into sub-metrics
2. **Slice** by North Star dimensions to isolate the driver
3. **Cross-tab** dimensions to find interaction effects
4. **Quantify** the impact with formula and caveats

See [analytics-deep-dive](../analytics-deep-dive/SKILL.md) for the full methodology.
See [analytics-insight-generation](../analytics-insight-generation/SKILL.md) for insight documentation templates.

## Phase 6: Present

Structure the README as a stakeholder report:

1. **Background & Overview** — Dataset, tech stack, audience, business questions
2. **Data Structure** — Schema diagram, pipeline flowchart, quality notes
3. **Executive Summary** — Key metrics table, headline findings
4. **Insights Deep Dive** — Findings by theme with supporting data
5. **Recommendations** — Prioritized actions with expected impact

See [dash-dashboard-framework](../dash-dashboard-framework/SKILL.md) for dashboard design.
See [portfolio-dashboard-build](../portfolio-dashboard-build/SKILL.md) for portfolio-specific presentation standards.

## Verification

- [ ] All scripts run end-to-end without errors
- [ ] Row counts reconcile between raw and modeled data
- [ ] KPI values match across views and reports
- [ ] Every finding has a "so what?" for a named stakeholder
- [ ] Data quality issues documented with decisions

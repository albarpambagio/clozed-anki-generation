---
name: portfolio-dashboard-build
description: Build portfolio-ready data dashboards with stakeholder-level README, star schema, KPIs, and insights. Use when creating data portfolio projects, analytics demos, or case studies for job applications or professional showcases.
---

# Portfolio Dashboard Build

Build a portfolio-ready analytics dashboard that demonstrates technical skill and business thinking.

## Structure

```
project/
├── data/           # Source data (CSV files)
├── sql/            # All SQL + Python scripts
│   ├── 01_create_tables.sql
│   ├── load_data_v2.py        # ETL: CSV → PostgreSQL
│   ├── phase2_cleaning_eda.py # Data quality + EDA
│   ├── phase3_starschema.py   # Star schema views
│   ├── phase4_kpis.py         # KPI aggregations
│   ├── phase5_funnel.py       # Funnel/advanced analysis (optional)
│   └── phase6_advanced.py     # Segmentation, cohort (optional)
├── logs/
│   ├── phase1_setup.log.md
│   ├── phase2_cleaning_eda.log.md
│   ├── phase3_starschema.log.md
│   └── insights.md            # SCAN Framework insights
├── docs/
│   ├── dashboard_guide.md     # Page-by-page walkthrough
│   ├── dash_framework.md      # DASH design framework
│   ├── INTERVIEW_TALKING_POINTS.md
│   ├── archive/               # Deprecated or historical docs
│   └── screenshots/           # Dashboard images (by user)
├── .gitkeep
└── README.md                  # Stakeholder-facing report
```

## README as Stakeholder Report

The README is the most important file. Structure it as a business report:

1. **Background & Overview** — Dataset, tech stack, stakeholder audience, business questions
2. **Data Structure** — Star schema diagram (mermaid), pipeline, quality notes
3. **Executive Summary** — Key metrics table, headline findings
4. **Insights Deep Dive** — Findings by theme with supporting data
5. **Recommendations** — Actionable, prioritized, with expected impact

### Quick Start Section

Include setup instructions:

```bash
# 1. Download dataset
kaggle datasets download -d source/dataset -p ./data --unzip

# 2. Set up database
python sql/load_data_v2.py
python sql/phase3_starschema.py
python sql/phase4_kpis.py

# 3. Connect Power BI
# Server: localhost:5433, Database: project_db
```

## Documentation Standards

### DASH Framework (docs/dash_framework.md)

Document design decisions:
- **D**ecision — What decision does each page enable?
- **A**udience — Who is this for at different technical levels?
- **S**ignal — Top metrics per page
- **H**ierarchy — Visual hierarchy rules

### Dashboard Guide (docs/dashboard_guide.md)

Page-by-page walkthrough with:
- KPI cards, visuals, business narrative
- Color palette and formatting rules

### Interview Talking Points (docs/INTERVIEW_TALKING_POINTS.md)

Q&A preparation covering:
- Project walkthrough, technical decisions, data challenges
- Key insights, recommendations, business impact
- Behavioral questions

## Polish Checklist (docs/archive/POLISH_CHECKLIST.md)

Before declaring portfolio complete:

- [ ] README tells a story (Background → Data → Insights → Recommendations)
- [ ] Star schema designed with mermaid ER diagram
- [ ] Data pipeline documented with mermaid flowchart
- [ ] All SQL scripts run without errors
- [ ] Data quality issues documented in logs
- [ ] Dashboard guide for each page
- [ ] DASH framework documented
- [ ] Interview talking points prepared
- [ ] Data source credited
- [ ] No hashtags in markdown leftovers

---
name: portfolio-dashboard-build
description: Build portfolio-ready data dashboards with stakeholder-level README, star schema, KPIs, and insights. Use when creating data portfolio projects, analytics demos, or case studies for job applications or professional showcases.
---

# Portfolio Dashboard Build

Build a portfolio-ready analytics dashboard that demonstrates technical skill and business thinking.

## Project Structure

```
project/
├── data/           # Source CSV files (gitignored if large)
├── sql/            # All SQL + Python scripts
│   ├── 01_create_tables.sql
│   ├── load_data.py               # ETL: CSV → PostgreSQL
│   ├── phase2_cleaning_eda.py     # Data quality + EDA
│   ├── phase3_starschema.py       # Star schema views
│   ├── phase4_kpis.py             # KPI aggregations
│   ├── phase5_funnel.py           # Advanced/funnel analysis (optional)
│   └── phase6_advanced.py         # Segmentation, cohort (optional)
├── logs/
│   ├── phase1_setup.log.md
│   ├── phase2_cleaning_eda.log.md # Data quality issues
│   ├── phase3_starschema.log.md
│   └── insights.md                # SCAN framework findings
├── docs/
│   ├── powerbi_build_guide.md     # Page-by-page build instructions
│   ├── dash_framework.md          # DASH design framework
│   ├── INTERVIEW_TALKING_POINTS.md # Interview Q&A prep
│   ├── archive/                   # Superseded docs
│   │   └── POLISH_CHECKLIST.md
│   └── screenshots/               # Dashboard images (by user)
├── .gitignore
└── README.md                      # Stakeholder-facing report
```

### File Purpose Reference

| File | Purpose | Audience |
|------|---------|----------|
| `README.md` | Stakeholder report, project overview | Recruiters, peers |
| `docs/powerbi_build_guide.md` | Page-by-page dashboard build guide | Developers, reviewers |
| `docs/dash_framework.md` | Design decisions and methodology | Developers, reviewers |
| `docs/INTERVIEW_TALKING_POINTS.md` | Q&A prep for interviews | Self |
| `docs/archive/POLISH_CHECKLIST.md` | Polish status tracker | Self |
| `logs/insights.md` | SCAN framework findings | Self, reviewers |
| `sql/phase*.py` | Sequential analysis scripts | Developers |

### Archive Rules

Move to `docs/archive/` when:
- Superseded by a newer version
- It is a temporary tracker or checklist
- Documents a completed process (not ongoing reference)

Keep in `docs/` when:
- Actively referenced during interviews
- Explains how the dashboard works
- Documents design decisions

## README as Stakeholder Report

The README is the most important file. Structure it as a business report:

1. **Background & Overview** — Dataset, tech stack, stakeholder audience, business questions
2. **Data Structure** — Star schema diagram (mermaid), pipeline, quality notes
3. **Executive Summary** — Key metrics table, headline findings
4. **Insights Deep Dive** — Findings by theme with supporting data
5. **Recommendations** — Actionable, prioritized, with expected impact
6. **Technical Implementation** — SQL scripts reference, quick start, project files

### Quick Start Section

Include setup instructions:

```bash
# 1. Download dataset
kaggle datasets download -d source/dataset -p ./data --unzip

# 2. Set up database
python sql/load_data.py
python sql/phase3_starschema.py
python sql/phase4_kpis.py

# 3. Connect dashboard
# Server: localhost:5433, Database: project_db
```

## Documentation Standards

### DASH Framework (docs/dash_framework.md)

See [dash-dashboard-framework](../dash-dashboard-framework/SKILL.md) for the full DASH framework.

### Dashboard Build Guide (docs/powerbi_build_guide.md)

Page-by-page instructions with:
- Data model relationships
- SQL views reference
- KPI card definitions
- Visual configuration per page
- Slicer setup

### Interview Talking Points (docs/INTERVIEW_TALKING_POINTS.md)

See [interview-prep-documentation](../interview-prep-documentation/SKILL.md) for the full template.

## Polish Checklist

Before declaring portfolio complete:

- [ ] README tells a story (Background → Data → Insights → Recommendations)
- [ ] Star schema designed with mermaid ER diagram
- [ ] Data pipeline documented with mermaid flowchart
- [ ] All SQL scripts run without errors
- [ ] Data quality issues documented in logs
- [ ] Dashboard guide with page-by-page build instructions
- [ ] DASH framework documented
- [ ] Interview talking points prepared
- [ ] Data source credited
- [ ] No hashtags in markdown leftovers
- [ ] All markdown files render correctly
- [ ] File paths in README match actual structure
- [ ] No empty directories (use .gitkeep if needed)

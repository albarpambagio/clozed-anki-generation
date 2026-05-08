---
name: docs-archive-organization
description: Structure and organize documentation for data analytics portfolio projects. Use when setting up project documentation, organizing docs folders, archiving outdated materials, or ensuring consistent file structure across multiple projects.
---

# Docs Archive Organization

Structure documentation for maintainable, portfolio-ready projects.

## Standard Directory Layout

```
project/
├── docs/
│   ├── dashboard_guide.md          # Page-by-page walkthrough
│   ├── dash_framework.md           # DASH design framework
│   ├── INTERVIEW_TALKING_POINTS.md # Interview Q&A prep
│   └── archive/                    # Historical or superseded docs
│       ├── POLISH_CHECKLIST.md
│       └── [other_archived].md
├── logs/
│   ├── phase1_setup.log.md
│   ├── phase2_cleaning_eda.log.md  # Data quality issues
│   ├── phase3_starschema.log.md
│   └── insights.md                 # SCAN framework findings
├── sql/
│   ├── 01_create_tables.sql
│   ├── load_data_v2.py            # Primary ETL
│   └── phase[2-6]_*.py            # Sequential phase scripts
├── data/                           # CSV files
├── screenshots/                    # Dashboard images
└── README.md                      # Stakeholder report
```

## File Purpose Guidelines

| File | Purpose | Audience |
|------|---------|----------|
| `README.md` | Stakeholder report, project overview | Recruiters, peers |
| `docs/dashboard_guide.md` | Page-by-page dashboard walkthrough | Developers, reviewers |
| `docs/dash_framework.md` | Design decisions and methodology | Developers, reviewers |
| `docs/INTERVIEW_TALKING_POINTS.md` | Q&A prep for interviews | Self |
| `docs/archive/POLISH_CHECKLIST.md` | Polish status tracker | Self |
| `logs/insights.md` | SCAN framework findings | Self, reviewers |
| `sql/phase*.py` | Sequential analysis scripts | Developers |

## Archive Rules

Move to `docs/archive/` when:
- A file is superseded by a newer version
- It's a temporary tracker or checklist
- It documents a completed process (not ongoing reference)

Keep in `docs/` when:
- It's actively referenced during interviews
- It explains how the dashboard works
- It documents design decisions

## Cleanup

Before finalizing project structure:

- [ ] Remove empty folders (use .gitkeep if needed)
- [ ] Check all markdown files render correctly
- [ ] Verify no trailing hashtags in headers
- [ ] Confirm file paths in README match actual structure
- [ ] Remove debug scripts and test files

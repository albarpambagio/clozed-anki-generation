# AI Agent Skills

Centralized collection of reusable AI agent skills for data analytics, dashboards, documentation, and portfolio projects. Each skill maps to a specific analytical framework or workflow phase.

## Structure

```
skills/
├── project-scaffolding/           # READY framework — project assessment & scoping
├── data-analytics-workflow/       # Industry-agnostic end-to-end pipeline
├── ecommerce-analytics-workflow/  # E-commerce specialization (references generic pipeline)
├── analytics-insight-generation/  # SCAN framework — structured insight generation
├── analytics-deep-dive/           # North Star decomposition & cross-tab methodology
├── data-quality-assessment/       # CLEAN framework — data quality & cleaning
├── star-schema-design/            # Fact + dimension table patterns
├── data-pipeline-automation/      # Python ETL patterns for CSV → PostgreSQL
├── dash-dashboard-framework/      # DASH framework — stakeholder dashboard design
├── portfolio-dashboard-build/     # Portfolio presentation & documentation standards
├── interview-prep-documentation/  # Interview Q&A prep for data projects
├── mermaid-diagram-generation/    # Mermaid.js diagrams for technical docs
└── clozed-anki-generation/        # Anki flashcard generation for spaced repetition
```

### Skill Relationships

Some skills build on others. The general-to-specific hierarchy:

```
data-analytics-workflow (generic pipeline)
├── project-scaffolding          ← scope the project
├── data-pipeline-automation     ← Phase 1: setup
├── data-quality-assessment      ← Phase 2: clean (CLEAN)
├── star-schema-design           ← Phase 3: model
├── analytics-insight-generation ← Phase 5: analyze (SCAN)
├── analytics-deep-dive          ← Phase 5: root cause discovery
└── portfolio-dashboard-build    ← Phase 6: present
    ├── dash-dashboard-framework ← DASH design
    └── interview-prep-documentation ← interview readiness

ecommerce-analytics-workflow (domain specialization)
└── delegates to all of the above per phase
```

## Usage

Copy a skill to your `.opencode/skills/` directory or configure your agent to reference this repo directly. Skills follow the Claude Agent Skills format.

## Skills Overview

| Skill | Framework | Phase |
|-------|-----------|-------|
| [project-scaffolding](skills/project-scaffolding/SKILL.md) | READY | Scope |
| [data-analytics-workflow](skills/data-analytics-workflow/SKILL.md) | — | End-to-end (generic) |
| [ecommerce-analytics-workflow](skills/ecommerce-analytics-workflow/SKILL.md) | — | End-to-end (e-commerce) |
| [data-quality-assessment](skills/data-quality-assessment/SKILL.md) | CLEAN | Clean |
| [star-schema-design](skills/star-schema-design/SKILL.md) | — | Model |
| [data-pipeline-automation](skills/data-pipeline-automation/SKILL.md) | — | Setup |
| [analytics-insight-generation](skills/analytics-insight-generation/SKILL.md) | SCAN | Analyze |
| [analytics-deep-dive](skills/analytics-deep-dive/SKILL.md) | North Star | Analyze (deep) |
| [dash-dashboard-framework](skills/dash-dashboard-framework/SKILL.md) | DASH | Present |
| [portfolio-dashboard-build](skills/portfolio-dashboard-build/SKILL.md) | — | Present |
| [interview-prep-documentation](skills/interview-prep-documentation/SKILL.md) | — | Present |
| [mermaid-diagram-generation](skills/mermaid-diagram-generation/SKILL.md) | — | Utility |
| [clozed-anki-generation](skills/clozed-anki-generation/SKILL.md) | — | Utility |

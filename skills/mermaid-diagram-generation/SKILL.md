---
name: mermaid-diagram-generation
description: Create Mermaid.js diagrams for technical documentation including ER diagrams, flowcharts, and graph layouts. Use when documenting data models, pipelines, architectures, or any process flow in markdown-based projects.
---

# Mermaid Diagram Generation

Create clear, maintainable diagrams for technical documentation using Mermaid.js syntax.

## Diagram Types

### ER Diagram (Data Models)

Best for: Star schemas, entity relationships, database models

```mermaid
erDiagram
    dim_parent ||--o{ fact_child : "foreign_key FK"

    dim_parent {
        string id PK
        string name
        string category
    }

    fact_child {
        string event_id PK
        string parent_id FK
        int date_key FK
        float measure
    }
```

Key rules:
- `||--o{` means one-to-many (parent to child)
- PK marks primary key, FK marks foreign key
- Fields grouped by entity with type annotation

### Flowchart (Pipelines & Processes)

Best for: Data pipelines, workflows, ETL sequences

```mermaid
flowchart LR
    A[Source Data] --> B[Script 1]
    B --> C[Transform 1]
    C --> D[Script 2]
    D --> E[Transform 2]
    E --> F[Output]
```

Subdividing with subgraphs:

```mermaid
flowchart LR
    subgraph Extract
        A[CSV Files] --> B[load.py]
    end
    subgraph Transform
        B --> C[clean.py]
        C --> D[model.py]
    end
    subgraph Load
        D --> E[Power BI]
    end
```

### Flowchart with Parallel Paths

Best for: Multi-source pipelines

```mermaid
flowchart LR
    A[Source A] --> C[Combine]
    B[Source B] --> C
    C --> D[Clean]
    D --> E[Output]
```

### Graph / Hierarchy

Best for: Page structures, navigation, org charts

```mermaid
graph TD
    subgraph Top
        A[Page Title]
    end
    subgraph Middle
        B[KPI Row]
        C[Charts]
    end
    subgraph Bottom
        D[Detail Table]
    end
    A --> B --> C --> D
```

## Syntax Guidelines

- Use `A --> B` for directional flow, `A --- B` for undirected
- Use `A -->|Label| B` for labeled edges
- Use `A -.-> B` for dashed lines (optional paths)
- Use `A == > B` for thick lines (emphasis)
- Use `style A fill:#f9f,stroke:#333` for custom styling
- Use `<br/>` for multi-line node text
- Use backticks inside node text: `` `code` ``

## When to Use Each Type

| Use Case | Diagram Type | Notes |
|----------|-------------|-------|
| Database schema | `erDiagram` | Shows relationships clearly |
| Data pipeline | `flowchart LR` | Left-to-right reads naturally |
| Process/decision | `flowchart TD` | Top-down for sequential steps |
| Page structure | `graph TD` | Hierarchy visualization |
| Architecture | `flowchart LR` with subgraphs | Group by layer |

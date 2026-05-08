---
name: data-pipeline-automation
description: Build Python ETL pipelines for loading CSV data into PostgreSQL with error handling, logging, and verification. Use when automating data loading from flat files into relational databases for analytics projects.
---

# Data Pipeline Automation

Build reliable Python ETL scripts for loading CSV data into PostgreSQL.

## ETL Script Pattern

```python
import psycopg2
from psycopg2.extras import execute_values
import pandas as pd

DB_CONFIG = {
    "host": "localhost",
    "port": 5433,
    "dbname": "your_db",
    "user": "postgres",
    "password": "your_password"
}

conn = psycopg2.connect(**DB_CONFIG)
cur = conn.cursor()
```

## Load CSV to Table

```python
def load_csv_to_table(filepath, table_name, conn):
    """Load CSV into PostgreSQL. Creates table from CSV headers if needed."""
    df = pd.read_csv(filepath, dtype=str)
    df = df.where(pd.notna(df), None)

    cols = ", ".join([f'"{c}" TEXT' for c in df.columns])
    cur = conn.cursor()
    cur.execute(f"DROP TABLE IF EXISTS {table_name} CASCADE")
    cur.execute(f"CREATE TABLE {table_name} ({cols})")

    values = [tuple(row) for row in df.to_numpy()]
    insert_sql = f"INSERT INTO {table_name} ({', '.join('"' + c + '"' for c in df.columns)}) VALUES %s"
    execute_values(cur, insert_sql, values)
    conn.commit()

    print(f"Loaded {len(df)} rows into {table_name}")
```

## Pipeline Structure

Organize scripts sequentially by phase:

```
sql/
├── load_data.py           # Extract + load all CSVs to raw tables
├── phase2_cleaning_eda.py # Transform: clean, profile, log issues
├── phase3_starschema.py   # Model: create star schema views
├── phase4_kpis.py         # Aggregate: create KPI views
└── phase5_advanced.py     # Enrich: segmentation, cohorts
```

## Logging Pattern

Each phase logs to `logs/`:

```python
import logging
logging.basicConfig(
    filename="logs/phase1_setup.log.md",
    level=logging.INFO,
    format="%(asctime)s | %(levelname)s | %(message)s"
)
```

## Verification

After each load step:

- [ ] Row count matches between CSV and database table
- [ ] Primary keys are unique and not null
- [ ] Date columns parse correctly
- [ ] Foreign key relationships resolve (no orphan records)

## Anti-Patterns

- **Loading everything in one script**: Phase scripts are easier to debug and restart
- **Hardcoded passwords**: Use environment variables or .env files
- **Silent failures**: Log all errors with stack traces
- **Modifying raw data**: Keep raw tables untouched, transform in views
- **Skipping type casting**: Load as TEXT initially, cast in views for flexibility

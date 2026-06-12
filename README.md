# hello-data

Personal data engineering sandbox — a `uv`-managed Python 3.12 project for exploring pandas and DuckDB locally.

## What's this?

A lightweight dev environment for:
- Prototyping pandas transformations and data pipelines
- Writing analytical SQL via DuckDB (in-process, no server needed)
- Testing patterns before applying them to larger projects

Pairs with a persistent DuckDB playground database connected via DBeaver for ad-hoc querying.

## Stack

| Tool | Version | Role |
|------|---------|------|
| [uv](https://github.com/astral-sh/uv) | latest | Project & package manager |
| [pandas](https://pandas.pydata.org/) | 3.x | DataFrame manipulation |
| [DuckDB](https://duckdb.org/) | 1.5+ | In-process analytical SQL |
| Python | 3.12 | Runtime |

## Setup

```bash
git clone https://github.com/MoazReda/hello-data.git
cd hello-data
uv sync        # creates .venv and installs deps
uv run main.py
```

## Quick start

```python
import duckdb
import pandas as pd

# In-memory DuckDB — query a DataFrame directly
con = duckdb.connect()
df = pd.DataFrame({"city": ["Cairo", "Alex"], "pop_m": [21, 5]})
result = con.execute("SELECT * FROM df ORDER BY pop_m DESC").df()
print(result)
```

## Notes

Part of a local data/AI development environment on Windows 11. Python managed entirely via `uv` — no conda, no global pip installs.

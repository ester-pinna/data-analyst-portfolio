# Repurchase Cycle Analysis

Anonymized client data from a D2C apparel e-commerce business. This mini-project asks one question: is a fixed Win Back threshold of 210 days since the last order a good fit for how customers actually repurchase? It measures the real repurchase cycle, checks when inactive customers come back after an email broadcast, and ends with recommendations for a multi-step Win Back flow.

## Data source
Derived from real client data, with customer personal data removed before use here — see [`data/raw/SOURCE.md`](data/raw/SOURCE.md) for details on what was removed or transformed.

## Structure
- `data/raw` — description of the original data source (the raw file is not published)
- `data/processed` — anonymized orders used by the analysis (`orders_anonymized.csv`)
- `01-repurchase-cycle` — analysis notebook and presentation

## Projects
1. [Repurchase Cycle Analysis](01-repurchase-cycle/repurchase_cycle.ipynb) — days between consecutive orders, comparison with the 210-day threshold, customers who come back after a broadcast, and recommendations
2. [Presentation (PDF)](01-repurchase-cycle/repurchase_cycle_presentation.pdf) — all results and recommendations in one place

## Tools
Python (pandas, matplotlib) · Databricks

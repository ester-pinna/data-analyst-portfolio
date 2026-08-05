# Winery E-commerce Analysis

Anonymized client data from a wine e-commerce business. This mini-project follows 
the full pipeline: data cleaning → business-question-driven analysis → recommendation.

## Data source

Derived from real client data, fully anonymized before use here — see 
[`data/raw/SOURCE.md`](./data/raw/SOURCE.md) for details on what was removed/anonymized.

## Structure

- [`01-data-cleaning`](./01-data-cleaning) — cleaning and preparation of the raw dataset
- `02-...`, `03-...` — one analysis per business question, built on the cleaned dataset

## Projects

1. **[Data Cleaning](./01-data-cleaning)** — handling duplicates, missing values, standardizing categorical fields; produces the cleaned dataset used by all analyses below

*Analysis projects in progress — updated regularly.*

## Tools

Python · SQL · Databricks

# Jade Trend Research Workspace

This directory stores the working assets for the 2027 jade trend research project.

## Purpose

The workspace supports a layered research workflow that combines:

- core jade account sampling,
- keyword-driven Xiaohongshu discovery,
- adjacent-category comparison,
- manual image review,
- normalized tagging and scoring.

## Directory Layout

- `raw/`: original exports and crawl outputs grouped by run date and source pool
- `normalized/`: cleaned tables, registries, and coding-ready structured files
- `images/`: downloaded or cached representative product images for review
- `analysis/`: research rubrics, sample definitions, keyword systems, templates, and findings

## Naming Conventions

- Use date-stamped filenames when storing collection outputs, for example `2026-03-22_pool-a_account-name.jsonl`.
- Prefix source pools consistently:
  - `pool_a` for core jade accounts
  - `pool_b` for keyword-result discovery
  - `pool_c` for adjacent-category accounts
- Keep raw files immutable after collection. If data needs cleanup, write the cleaned version into `normalized/`.
- Use lowercase ASCII filenames for new research artifacts unless an existing project convention requires otherwise.

## Core Control Files

- `sample_registry.csv`: master registry of all planned and collected sources
- `analysis/sample_frame.md`: sample design and inclusion logic
- `analysis/keyword_system.md`: grouped search language and keyword logic
- `normalized/keyword_registry.csv`: the working keyword list for collection

## Working Rule

For high-value product notes, image review is mandatory before drawing product or trend conclusions. If the image cannot be read clearly, mark the sample incomplete instead of forcing analysis.

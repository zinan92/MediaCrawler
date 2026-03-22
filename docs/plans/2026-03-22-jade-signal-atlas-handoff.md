# Jade Signal Atlas Handoff

**Project name:** Jade Signal Atlas  
**Chinese reference name:** 翡翠信号图谱

## Current Working Context

- Worktree: `/Users/wendy/work/content-co/MediaCrawler-jade-trend-research`
- Branch: `feat/jade-trend-research-foundation`
- Remote: `origin https://github.com/zinan92/MediaCrawler.git`
- Date: `2026-03-22`

## What Was Completed Today

### Research foundation

- Defined the overall research design for the 2027 jade trend study.
- Wrote the execution plan that breaks the work into concrete tasks.
- Created the isolated research workspace under `data/research/jade_trends/`.

### Tasks 1-3 completed

1. Research workspace scaffolding
2. Sample frame design
3. Keyword system design

## Files Created

### Planning docs

- `docs/plans/2026-03-22-jade-trend-research-design.md`
- `docs/plans/2026-03-22-jade-trend-research-plan.md`
- `docs/plans/2026-03-22-jade-signal-atlas-handoff.md`

### Research workspace

- `data/research/jade_trends/README.md`
- `data/research/jade_trends/sample_registry.csv`
- `data/research/jade_trends/analysis/sample_frame.md`
- `data/research/jade_trends/analysis/keyword_system.md`
- `data/research/jade_trends/normalized/keyword_registry.csv`

## Important Research Decisions

- Primary business goal: support next-year jade product and design decisions.
- Core current audience: women aged 30-45.
- Growth audience: women aged 25-35 and younger style-forward buyers.
- Main price band: `3000-8000 RMB`.
- Strategic themes to test: `18K gold`, `dopamine color`, `agarwood + jade`.
- Research structure: jade category as trunk, adjacent-category signals as growth layer.

## Key Improvements Added During Review

- Added real jade market price-language keywords such as `小千`, `中千`, `大千`, `小万`, `预算5k`.
- Added account-size stratification: `head`, `mid`, `emerging`.
- Expanded the sample registry schema with `source_class`, `account_tier`, and `priority`.
- Normalized pool naming to `pool_a`, `pool_b`, `pool_c`.
- Added missing seed keywords such as `翡翠项链设计` and `东方轻珠宝`.

## Verified State

- Git worktree is clean after the current commits.
- The last three commits establish Tasks 1-3.
- Research workspace folders and files exist.
- Keyword registry contains the current grouped seed set for the pilot.

## Known Environment Limitation

- `uv run pytest ...` hit a local `uv` panic in this environment.
- System `python3` does not currently have `pytest` installed.
- Because of that, completion status today was verified through filesystem and git-state checks, not through project test execution.

## Recommended Next Step

Continue with Tasks 4-6:

1. define the normalized note schema
2. define the image review rubric
3. define the collection workflow

## Resume Prompt

If resuming tomorrow, start from:

> Open the worktree at `/Users/wendy/work/content-co/MediaCrawler-jade-trend-research`, read `docs/plans/2026-03-22-jade-trend-research-plan.md` and `docs/plans/2026-03-22-jade-signal-atlas-handoff.md`, then continue with Tasks 4-6 for Jade Signal Atlas.

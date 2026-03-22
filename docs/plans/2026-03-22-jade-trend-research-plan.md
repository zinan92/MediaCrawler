# Jade Trend Research Implementation Plan

> **For Claude:** REQUIRED SUB-SKILL: Use superpowers:executing-plans to implement this plan task-by-task.

**Goal:** Build an evidence-based research workflow that identifies 2027 jade product and design trends for the 3000-8000 RMB price band, with special attention to 18K gold, dopamine color, and agarwood + jade opportunities.

**Architecture:** The workflow uses Xiaohongshu as the primary signal source, combines account-based and keyword-based collection, adds adjacent-category comparison, then normalizes everything into a shared tagging and scoring model. The final deliverables are a trend map, a product priority list, and design briefs.

**Tech Stack:** MediaCrawler, Xiaohongshu JSONL/Excel exports, spreadsheet or SQLite for labeling, manual image review, lightweight analysis scripts, markdown research synthesis

---

### Task 1: Create the research workspace

**Files:**
- Create: `docs/plans/2026-03-22-jade-trend-research-design.md`
- Create: `docs/plans/2026-03-22-jade-trend-research-plan.md`
- Create: `data/research/jade_trends/README.md`
- Create: `data/research/jade_trends/sample_registry.csv`

**Step 1: Create the research folders**

Create:

- `data/research/jade_trends/`
- `data/research/jade_trends/raw/`
- `data/research/jade_trends/normalized/`
- `data/research/jade_trends/images/`
- `data/research/jade_trends/analysis/`

**Step 2: Create a registry file for all sample sources**

Create `data/research/jade_trends/sample_registry.csv` with columns:

```csv
pool,source_type,platform,name,handle_or_keyword,url_or_id,category,status,notes
```

**Step 3: Create a research readme**

Create `data/research/jade_trends/README.md` describing folder purpose and naming conventions.

**Step 4: Verify the workspace exists**

Run: `find data/research/jade_trends -maxdepth 2 -type d | sort`

Expected: all research folders are listed

**Step 5: Commit**

```bash
git add docs/plans/2026-03-22-jade-trend-research-design.md docs/plans/2026-03-22-jade-trend-research-plan.md data/research/jade_trends
git commit -m "docs: add jade trend research design and workspace plan"
```

### Task 2: Define the sample frame

**Files:**
- Modify: `data/research/jade_trends/sample_registry.csv`
- Create: `data/research/jade_trends/analysis/sample_frame.md`

**Step 1: Write the target sample counts**

Document:

- `30-50` jade accounts
- `20-30` adjacent-category accounts
- `40-80` keywords across grouped themes

**Step 2: Define source pools**

Add rows for:

- `pool_a_core_jade_accounts`
- `pool_b_keyword_results`
- `pool_c_adjacent_category_accounts`

**Step 3: Define account-class tags**

Use:

- `commercial_conversion`
- `aesthetic_editorial`
- `young_experimental`

**Step 4: Define adjacent-category tags**

Use:

- `18k_light_jewelry`
- `pearls`
- `colored_gemstones`
- `agarwood_eastern_accessories`
- `fashion_accessories`

**Step 5: Verify registry completeness**

Run: `wc -l data/research/jade_trends/sample_registry.csv`

Expected: line count grows as rows are added

**Step 6: Commit**

```bash
git add data/research/jade_trends/sample_registry.csv data/research/jade_trends/analysis/sample_frame.md
git commit -m "docs: define jade trend sample frame"
```

### Task 3: Build the keyword system

**Files:**
- Create: `data/research/jade_trends/analysis/keyword_system.md`
- Create: `data/research/jade_trends/normalized/keyword_registry.csv`

**Step 1: Create the keyword groups**

Use these top-level groups:

- `jade_basics`
- `modern_jade_design`
- `material_combination`
- `style_and_scene`
- `price_and_gifting`
- `adjacent_categories`

**Step 2: Seed initial keywords**

Include examples such as:

```text
翡翠吊坠
翡翠耳饰
18k金翡翠
翡翠叠戴
翡翠项链设计
沉香 翡翠
东方轻珠宝
多巴胺 珠宝
珍珠 项链
彩色宝石 项链
```

**Step 3: Create the keyword registry**

Use columns:

```csv
group_name,keyword,priority,notes
```

**Step 4: Review for overlap and redundancy**

Remove near-duplicate keywords unless they intentionally target a different search behavior.

**Step 5: Commit**

```bash
git add data/research/jade_trends/analysis/keyword_system.md data/research/jade_trends/normalized/keyword_registry.csv
git commit -m "docs: define jade trend keyword system"
```

### Task 4: Define the normalized note schema

**Files:**
- Create: `data/research/jade_trends/analysis/note_schema.md`
- Create: `data/research/jade_trends/normalized/note_schema.csv`

**Step 1: Define raw metadata fields**

Include:

- `platform`
- `account_name`
- `account_type`
- `note_id`
- `note_url`
- `published_at`
- `title`
- `desc`
- `liked_count`
- `collected_count`
- `comment_count`
- `share_count`
- `image_count`
- `video_url_present`
- `tag_list`

**Step 2: Define coding fields**

Include:

- `product_category`
- `jade_color_family`
- `transparency_level`
- `shape_language`
- `material_combination`
- `metal_language`
- `style_scene`
- `visual_system`
- `narrative_strategy`
- `core_audience_fit`
- `young_growth_fit`
- `price_band_fit`

**Step 3: Define evidence fields**

Include:

- `image_strength_score`
- `interaction_strength_score`
- `comment_signal_score`
- `cross_category_resonance_score`
- `total_weighted_score`
- `coding_confidence`

**Step 4: Define completion flags**

Include:

- `image_review_complete`
- `comment_review_complete`
- `needs_followup`

**Step 5: Commit**

```bash
git add data/research/jade_trends/analysis/note_schema.md data/research/jade_trends/normalized/note_schema.csv
git commit -m "docs: define normalized note schema for jade research"
```

### Task 5: Define the image-review rubric

**Files:**
- Create: `data/research/jade_trends/analysis/image_review_rubric.md`

**Step 1: Define mandatory review questions**

Every selected note should answer:

1. What is the product focal point?
2. Does the jade read modern, traditional, or mixed?
3. How does the metal or secondary material change the impression?
4. Does the piece feel premium for the target price band?
5. Would the current audience and younger audience react differently?

**Step 2: Define visual tags**

Add standard tags for:

- color contrast
- proportion
- layering logic
- finish quality
- boldness level
- Eastern versus contemporary tone

**Step 3: Define incomplete-case handling**

If the image cannot be accessed or interpreted clearly, mark the note incomplete instead of forcing coding.

**Step 4: Commit**

```bash
git add data/research/jade_trends/analysis/image_review_rubric.md
git commit -m "docs: add image review rubric for jade trend research"
```

### Task 6: Set the collection workflow

**Files:**
- Create: `data/research/jade_trends/analysis/collection_workflow.md`
- Create: `data/research/jade_trends/raw/collection_runs.csv`

**Step 1: Define collection order**

Sequence:

1. build account pool
2. collect account notes
3. build keyword pool
4. collect keyword-result notes
5. collect adjacent-category notes
6. collect comments for shortlisted notes
7. download or cache representative images

**Step 2: Define run logging**

Use columns:

```csv
run_date,pool,source_name,source_type,scope,status,output_path,notes
```

**Step 3: Define naming conventions**

Use date-stamped files and pool prefixes so later analysis can trace every sample back to source.

**Step 4: Commit**

```bash
git add data/research/jade_trends/analysis/collection_workflow.md data/research/jade_trends/raw/collection_runs.csv
git commit -m "docs: define jade trend collection workflow"
```

### Task 7: Create the scoring model

**Files:**
- Create: `data/research/jade_trends/analysis/scoring_model.md`
- Create: `data/research/jade_trends/normalized/trend_score_template.csv`

**Step 1: Define the four evidence buckets**

Use:

- `image_strength`
- `interaction_strength`
- `comment_signal_strength`
- `cross_category_resonance`

**Step 2: Define score scale**

Use `1-5` for each bucket.

**Step 3: Define weights**

Use:

- `image_strength = 0.30`
- `interaction_strength = 0.25`
- `comment_signal_strength = 0.20`
- `cross_category_resonance = 0.25`

**Step 4: Define confidence rules**

Require stronger evidence for a trend to be labeled `confirmed` than `emerging`.

**Step 5: Commit**

```bash
git add data/research/jade_trends/analysis/scoring_model.md data/research/jade_trends/normalized/trend_score_template.csv
git commit -m "docs: define jade trend scoring model"
```

### Task 8: Design the output templates

**Files:**
- Create: `data/research/jade_trends/analysis/trend_map_template.md`
- Create: `data/research/jade_trends/analysis/product_priority_template.md`
- Create: `data/research/jade_trends/analysis/design_brief_template.md`

**Step 1: Create the trend map template**

Fields:

- trend name
- description
- evidence summary
- audience fit
- price fit
- confidence level
- recommended action

**Step 2: Create the product priority template**

Buckets:

- `build_now`
- `test_capsule`
- `monitor`
- `avoid_for_now`

**Step 3: Create the design brief template**

Fields:

- target audience
- product type
- material mix
- color direction
- metal language
- silhouette
- emotional hook
- content cues

**Step 4: Commit**

```bash
git add data/research/jade_trends/analysis/trend_map_template.md data/research/jade_trends/analysis/product_priority_template.md data/research/jade_trends/analysis/design_brief_template.md
git commit -m "docs: add jade trend output templates"
```

### Task 9: Pilot the workflow on a small sample

**Files:**
- Create: `data/research/jade_trends/analysis/pilot_sample.md`
- Create: `data/research/jade_trends/normalized/pilot_notes.csv`
- Create: `data/research/jade_trends/analysis/pilot_findings.md`

**Step 1: Select a pilot sample**

Use:

- `3-5` jade accounts
- `10-15` keywords
- `3-5` adjacent-category accounts

**Step 2: Collect a small dataset**

Run the collection workflow and save outputs in the `raw/` folder.

**Step 3: Code `20-30` high-value notes manually**

Apply the note schema and image-review rubric.

**Step 4: Test the scoring model**

Make sure the scores separate confirmed signals from weak noise.

**Step 5: Document pilot findings and rubric changes**

Capture:

- missing fields
- ambiguous tags
- weak keywords
- scoring problems

**Step 6: Commit**

```bash
git add data/research/jade_trends/analysis/pilot_sample.md data/research/jade_trends/normalized/pilot_notes.csv data/research/jade_trends/analysis/pilot_findings.md
git commit -m "docs: add jade trend pilot research outputs"
```

### Task 10: Run the full study and synthesize conclusions

**Files:**
- Create: `data/research/jade_trends/analysis/final_trend_map.md`
- Create: `data/research/jade_trends/analysis/final_product_priorities.md`
- Create: `data/research/jade_trends/analysis/final_design_briefs.md`

**Step 1: Expand from pilot to full sample**

Collect the full account pool, keyword pool, and adjacent-category pool.

**Step 2: Normalize and code the shortlisted notes**

Prioritize the notes with the strongest product signal.

**Step 3: Score trend clusters**

Group notes into trend clusters and compute evidence-backed judgments.

**Step 4: Write the final synthesis**

Deliver:

- 2027 jade trend map
- prioritized product directions
- design briefs for top directions

**Step 5: Review strategic fit**

Check that recommendations fit:

- current 30-45 customer base
- younger growth directions
- 3000-8000 RMB price band

**Step 6: Commit**

```bash
git add data/research/jade_trends/analysis/final_trend_map.md data/research/jade_trends/analysis/final_product_priorities.md data/research/jade_trends/analysis/final_design_briefs.md
git commit -m "docs: add final jade trend research synthesis"
```

---
name: ace-tech-research
description: |
  Deep technology research with evidence tracking, multi-source search, and citation verification.
  Trigger: "调研", "research", "深入了解", or technology comparison requests.
  Default output: Chinese Simplified; code/terms in English.
allowed-tools:
  - Bash
  - Read
  - Write
  - Task
  - WebSearch
  - WebFetch
  - mcp__context7__resolve-library-id
  - mcp__context7__query-docs
  - mcp__exa__web_search_exa
  - mcp__exa__get_code_context_exa
  - mcp__open-websearch__search
  - mcp__open-websearch__fetchGithubReadme
  - mcp__mcp-deepwiki__deepwiki_fetch
---

# Technology Deep Research

Research topic: {{arguments}}

## Quick Start

1. Clarify the report spec and format contract
2. Build a research plan and query set
3. Collect evidence with multi-source search tools (multi-pass if needed)
4. Activity screening — filter low-quality projects
5. Triage sources and build an evidence table
6. Outline and section map
7. Determine deliverables (dual-doc or single report)
8. Multi-pass full drafting (parallel subagents)
9. UNION merge, enforce format compliance, verify citations
10. Present draft for human review and iterate

## Core Workflow

Copy this checklist and track progress:

```
Deep Research Progress:
- [ ] Step 1: Intake and format contract
- [ ] Step 2: Research plan and query set
- [ ] Step 3: Evidence collection (multi-source search)
- [ ] Step 3.5: Activity screening
- [ ] Step 4: Source triage and evidence table
- [ ] Step 5: Outline and section map
- [ ] Step 5.5: Determine deliverables
- [ ] Step 6: Multi-pass full drafting (parallel subagents)
- [ ] Step 7: UNION merge and format compliance
- [ ] Step 8: Evidence and citation verification
- [ ] Step 9: Present draft for human review and iterate
```

### Step 1: Intake and Format Contract

Establish the report requirements before any research:

- Confirm audience, purpose, scope, time range, and geography
- Lock output format: Markdown (default)
- Capture required sections and exact formatting rules
- Confirm citation style (inline URL is default for tech reports)
- Confirm length targets per section
- Ask for any existing style guide or sample report

**Format contract defaults (ace-tech-research specific):**
- Language: Chinese Simplified (中文简体)
- Code snippets, CLI commands, API names, library names: keep English
- Time focus: 2025-2026 (latest available)
- Citation style: inline URLs after claims

Create a concise report spec file:

```
Report Spec:
- Audience:
- Purpose:
- Scope:
- Time Range: 2025-2026 (default)
- Geography:
- Required Sections:
- Section Formatting Rules:
- Citation Style: inline URL (default)
- Output Format: Markdown
- Output Language: zh-CN (default)
- Length Targets:
- Tone:
- Must-Include Sources:
- Must-Exclude Topics:
- Must-Answer Questions: (user's specific questions, if any)
```

If a user provides a template or an example report, treat it as a hard constraint and mirror the structure.

If the user has specific questions, record them as a **"Must-Answer Questions"** list — these MUST be answered directly at the top of the report.

### Step 2: Research Plan and Query Set

Define the research strategy before calling tools:

- Break the main question into 3-7 subquestions
- Define key entities, keywords, and synonyms
- **Include both Chinese and English keyword variants** for each subquestion
- Identify primary sources vs secondary sources
- Define disqualifiers (outdated, low quality, opinion-only)
- Assemble a query set per section

Use [references/research_plan_checklist.md](references/research_plan_checklist.md) for guidance.

### Step 3: Evidence Collection (Multi-Source Search)

Use the **multi-source search tool matrix** to collect evidence and citations. Do NOT rely on a single search tool — diversify sources for comprehensive coverage.

#### Search Tool Matrix

| Tool | Best For | When to Use |
|---|---|---|
| `WebSearch` | Latest articles, news, blog posts | Always — primary discovery tool |
| `mcp__exa__web_search_exa` | High-quality web results with context | Supplement WebSearch for broader coverage |
| `mcp__mcp-deepwiki__deepwiki_fetch` | GitHub project deep documentation | When evaluating specific OSS projects |
| `mcp__context7__resolve-library-id` + `query-docs` | Framework/library official docs | When researching specific libraries/frameworks |
| `mcp__open-websearch__fetchGithubReadme` | Quick README retrieval | Quick screening of GitHub projects |
| `mcp__exa__get_code_context_exa` | Code-level context and examples | When code implementation details needed |
| `WebFetch` | Specific URL content retrieval | When a known URL needs scraping |
| `mcp__open-websearch__search` | Alternative web search (DuckDuckGo/Bing/Brave) | When WebSearch results are insufficient |

#### Multi-Pass Strategy

- Run multiple complete passes if coverage is uncertain
- Vary query phrasing and language (zh/en) to reduce blind spots
- Use different tools per pass for source diversity
- Preserve raw tool output in files for traceability

**File structure (recommended):**
```
research/<topic-name>/
  search_pass1.md
  search_pass2.md
  search_pass3.md
```

### Step 3.5: Activity Screening (MUST Do Before Comparison)

Before including any project/tool in the core comparison, verify:

- **Stars**: check GitHub stars (use search tools, not guesses)
- **Update frequency**: last commit date, release cadence
- **Commit count**: low commit count (< 20) may indicate a throwaway or toy project
- **Community validation**: is it recommended by others, or only self-promoted?

**Exclusion criteria** — move to footnote or "Excluded Projects" section, do NOT put in core comparison:

1. < 10 GitHub stars AND no sustained maintenance
2. Pure prompt wrapper with no meaningful logic or tooling
3. Self-promoted only (e.g. posted in awesome-lists with no external endorsement)
4. Stale one-off project: all commits concentrated in a very short burst AND last update > 30 days ago with zero follow-up activity (issues, releases, community discussion). Note: a brand-new project with recent burst activity should NOT be excluded — check age before applying this rule
5. Last updated > 12 months ago with no signs of active community
6. Miscategorized (e.g. a brainstorming tool listed as a research tool)

Always include a brief **"Excluded Projects"** table explaining why each was filtered out.

See [references/source_quality_rubric.md](references/source_quality_rubric.md) for source quality tiers.

### Step 4: Source Triage and Evidence Table

Normalize and score sources before drafting:

- De-duplicate sources across passes
- Score sources using [references/source_quality_rubric.md](references/source_quality_rubric.md)
- Build an evidence table mapping claims to sources

Evidence table minimum columns:

| Column | Description |
|---|---|
| Source ID | Unique identifier (S1, S2, ...) |
| Title | Source title |
| Publisher | Organization or author |
| Date | Publication date |
| URL | Direct link |
| Quality Tier | A / B / C per rubric |
| Notes | Relevance and reliability notes |

### Step 5: Outline and Section Map

Create an outline that enforces the format contract:

- Use the template in [references/research_report_template.md](references/research_report_template.md)
- Produce a section map with required elements per section
- Confirm ordering and headings match the report spec
- If evidence reveals important dimensions not in the original outline, adjust the structure
- If a subquestion has insufficient evidence, mark it as "⚠️ 证据不足" rather than fabricating content

### Step 5.5: Determine Deliverables

Based on the research topic, decide the output format:

- **Deployable / installable / usable technology** → produce TWO documents:
  1. **Overview report** (概览报告) — what it is, why it matters, pros/cons analysis
  2. **Hands-on guide** (上手指南) — how to deploy, configure, and use it (full step-by-step)
- **Pure concepts / theories / comparisons** → single overview report is sufficient
- If the user's request contains specific questions, answer them directly at the top of the report (e.g. a "Key Questions Answered" section)

#### Hands-on guide structure rules

- Organize by **user workflow**, NOT by knowledge category
- If there are multiple deployment methods / approaches, each MUST be a **complete, self-contained pipeline** from start to finish
- Readers should pick one approach and follow it top-to-bottom without jumping to other sections
- Shared configuration (e.g. API options) MUST be repeated inside each approach — do NOT extract into a separate chapter that forces readers to jump around
- Each step should include the exact commands, config snippets, and expected output
- Clearly label which approach each instruction belongs to (e.g. "方案 A-3", "方案 B-2")

See [references/research_report_template.md](references/research_report_template.md) for both templates.

### Step 6: Multi-Pass Full Drafting (Parallel Subagents)

Avoid single-pass drafting; generate multiple complete reports, then merge.

#### Preferred Strategy: Parallel Subagents (Complete Draft Each)

Use the Task tool to spawn parallel subagents with isolated context. Each subagent must:

- Load the report spec, outline, and evidence table
- Draft the FULL report (all sections)
- Enforce formatting rules and citation style

**Implementation pattern:**
```
Task(subagent_type="general-purpose", prompt="Draft complete report ...", run_in_background=false) -> version1.md
Task(subagent_type="general-purpose", prompt="Draft complete report ...", run_in_background=false) -> version2.md
Task(subagent_type="general-purpose", prompt="Draft complete report ...", run_in_background=false) -> version3.md
```

**Write drafts to files, not conversation context:**
```
research/<topic-name>/drafts/
  version1.md
  version2.md
  version3.md
```

### Step 7: UNION Merge and Format Compliance

Merge using UNION, never remove content without evidence-based justification:

- Keep all unique findings from all versions
- Consolidate duplicates while preserving the most detailed phrasing
- Ensure every claim in the merged draft has a cited source
- Enforce the exact section order, headings, and formatting
- Re-run formatting rules from [references/formatting_rules.md](references/formatting_rules.md)

### Step 8: Evidence and Citation Verification

Verify traceability:

- Every numeric claim has at least one source
- Every recommendation references supporting evidence
- No orphan claims without citations
- Dates and time ranges are consistent
- Conflicts are explicitly called out with both sources

Use [references/completeness_review_checklist.md](references/completeness_review_checklist.md).

### Step 9: Present Draft for Human Review and Iterate

Present the draft as a reviewable version:

- Emphasize that format compliance and factual accuracy need human review
- Accept edits to format, structure, and scope
- If the user provides another AI output, cross-compare and UNION merge

## Output Requirements

- Default language: **Chinese Simplified (中文简体)**
- Code snippets, CLI commands, API names, library names: **keep English**
- Respect the report spec and formatting rules
- Include a references section or bibliography with URLs

### File Output Rules

- Before writing, inspect the project directory structure (`ls` root and relevant subdirectories)
- Follow the existing directory organization conventions
- Place research files under `research/{topic}/` subdirectory (e.g. `research/tauri-2/`)
- Multiple documents about the same topic MUST live in the same subdirectory
- Keep naming and grouping consistent with sibling directories

## Reference Files

| File | When to Load |
|---|---|
| [research_report_template.md](references/research_report_template.md) | Build outline, draft structure, dual-doc templates |
| [formatting_rules.md](references/formatting_rules.md) | Enforce section formatting, citation rules, Chinese output rules |
| [source_quality_rubric.md](references/source_quality_rubric.md) | Score sources, triage, GitHub activity screening |
| [research_plan_checklist.md](references/research_plan_checklist.md) | Build research plan, query set, multi-source tool strategy |
| [completeness_review_checklist.md](references/completeness_review_checklist.md) | Review for coverage, citations, and compliance |

## Anti-Patterns

1. Single-pass drafting without parallel complete passes
2. Splitting passes by section instead of full report drafts
3. Ignoring the format contract or user template
4. Claims without citations or evidence table mapping
5. Mixing conflicting dates without calling out discrepancies
6. Copying external AI output without verification
7. Deleting intermediate drafts or raw research outputs
8. **Including unmaintained projects in core comparison** (bypassing activity screening)
9. **Relying solely on training data without real-time search** — MUST use search tools

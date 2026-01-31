# Formatting Rules

Use these rules to enforce strict report formatting.

## Language Rules

- **Default output language**: Chinese Simplified (中文简体)
- **Keep in English**: code snippets, CLI commands, API names, library names, framework names, technical acronyms
- **Mixed text**: Chinese prose with English technical terms inline (e.g. "使用 `npm install` 安装依赖")
- **Headers**: may use Chinese or English depending on context, but be consistent within a report

## Headings

- Use H1 for report title only
- Use H2 for top-level sections
- Use H3 for subsections
- Keep heading titles consistent with the report spec

## Section Order

- Follow the report spec order exactly
- Do not add or remove sections without approval

## Bullets and Tables

- Use bullets for lists of findings and actions
- Use tables for comparisons, metrics, or timelines
- Keep tables compact and label all columns
- Comparison tables MUST include: positioning, pros/cons, use cases, community activity

## Citations

- Default citation style: inline URL after the claim
- Place citations immediately after the claim
- If a claim has multiple sources, list all relevant sources
- Format: `...claim text ([source](url))`

## Terminology

- Define key terms once and reuse consistently
- Preserve technical terms in English
- First occurrence of a technical term: provide brief Chinese explanation in parentheses if non-obvious

## Formatting Hygiene

- Avoid mixed numbering styles in the same section
- Avoid inline URLs in prose unless the spec requires it (use markdown links)
- Do not embed new assets unless requested
- Use consistent emoji markers for confidence levels (🟢🟡🔴)

## Time Range

- Focus on 2025-2026 data by default
- Explicitly mark information that may be outdated
- Use search tools for latest data — never rely solely on training knowledge

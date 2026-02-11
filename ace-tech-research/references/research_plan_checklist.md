# Research Plan Checklist

Use this checklist before starting evidence collection.

## Scope and Questions

- Define the primary research question
- Break into 3-7 subquestions
- Define scope boundaries and exclusions
- Define time range and geography (default: 2025-2026, global)

## Evidence Strategy

- Identify primary sources needed
- Identify secondary sources needed
- Define inclusion and exclusion criteria
- Define minimum number of sources per section

## Query Set

- Create query variants per subquestion
- **Include both Chinese and English variants** for each query
- Include synonyms and alternate terms
- Add disambiguating keywords

## Multi-Source Tool Strategy

Plan which tools to use for each subquestion:

| Subquestion | Primary Tool | Supplementary Tool | Language |
|---|---|---|---|
| Q1: ... | WebSearch | DeepWiki | en + zh |
| Q2: ... | Context7 | Exa | en |
| Q3: ... | WebSearch | fetchGithubReadme | en + zh |

### Tool Selection Guide

- **General knowledge / news / trends**: WebSearch, mcp__open-websearch__search
- **Specific GitHub project deep-dive**: mcp__mcp-deepwiki__deepwiki_fetch
- **Framework/library official docs**: mcp__context7__resolve-library-id + query-docs
- **Code examples and implementation**: mcp__exa__get_code_context_exa
- **Quick project screening**: mcp__open-websearch__fetchGithubReadme
- **High-quality curated results**: mcp__exa__web_search_exa
- **Specific URL content**: WebFetch

## Query Log Template

```
- Query: {query text}
- Tool: {tool used}
- Language: {en/zh}
- Intended section: {report section}
- Date run: {date}
- Results quality: {good/partial/poor}
- Notes: {observations}
```

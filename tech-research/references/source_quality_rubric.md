# Source Quality Rubric

Classify sources into tiers and prioritize higher quality evidence.

## Tier A (Highest)

- Primary sources: government data, standards bodies, peer-reviewed papers
- Official filings: annual reports, regulatory filings, audited statements
- First-party datasets with transparent methodology
- Official project documentation and release notes

## Tier B (Reliable)

- Reputable news organizations with editorial standards
- Industry analyst reports with clear methodology
- Company technical blogs with data and disclosures
- Well-maintained GitHub projects with active communities

## Tier C (Use Sparingly)

- Opinion pieces without evidence
- Marketing materials without verification
- Aggregators without clear sourcing
- Forum posts and social media (use only for sentiment/community signals)

## Exclusion Rules

- Exclude sources with no date or author
- Exclude sources that cannot be verified
- Exclude sources that are clearly outdated for the topic

## Conflict Handling

- Surface conflicting sources explicitly
- Prefer higher tier sources
- Note uncertainty when conflicts remain

## GitHub Project Activity Screening

In addition to source quality, apply these criteria when evaluating open-source projects:

### Include in Core Comparison (All Must Pass)

- GitHub stars: >= 10 (or strong external endorsement)
- Last commit: within 12 months
- Commit pattern: sustained activity (not a single burst)
- Community signals: issues, PRs, or discussions from external users

### Move to "Excluded Projects" Section

| Criterion | Threshold | Action |
|---|---|---|
| Stars | < 10 AND no maintenance | Exclude from core |
| Prompt wrapper | No meaningful logic | Exclude from core |
| Self-promoted only | No external endorsement | Exclude from core |
| Stale burst | All commits in short burst, inactive > 30 days | Exclude (unless brand new) |
| Abandoned | Last update > 12 months | Exclude from core |
| Miscategorized | Wrong category | Exclude from core |

### Quick Mode Simplified Screening

For Quick mode, check only:
- GitHub stars (>= 10)
- Last update date (within 12 months)

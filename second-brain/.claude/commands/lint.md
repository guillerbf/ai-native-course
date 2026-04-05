# Skill: Wiki Health Check

Run a health check on the wiki. Process articles in parallel where possible.

## Step 1: Inventory
Count all files in `wiki/summaries/`, `wiki/concepts/`, `wiki/queries/`, `wiki/briefings/`.
Read `wiki/_index.md`.

## Step 2: Structural checks (every article)
- Has a summary paragraph at the top?
- Has `## Sources` section?
- Has `## Related Articles` section?
- All `[[internal links]]` point to files that exist?

**Auto-fix:** Add empty `## Sources` or `## Related Articles` if missing.

## Step 3: Content checks (concept articles only)
- Cites at least 2 sources?
- Has `## Key Insights`?
- Any `TODO:` markers? (collect all)
- Under 200 words? (flag as "needs enrichment")

## Step 4: Coverage checks
- Which summaries have no linked concept article? → orphan summaries
- Which topics have only 1 article? → shallow coverage
- Which concept articles are not linked from anywhere? → disconnected

## Step 5: Contradiction detection (only if `$ARGUMENTS` == "deep")
Compare claims across concept articles. Flag conflicting statistics, contradictory assessments, or inconsistent definitions.

## Step 6: Freshness
Flag articles based entirely on sources older than 18 months.

## Step 7: Write health report

Save to `wiki/health-report.md`:

```
# Wiki Health Report — [date]

## Scorecard
| Check | Pass | Fail |
|-------|------|------|
| Summary paragraph | X/Y | X/Y |
| Sources section | X/Y | X/Y |
| Related Articles | X/Y | X/Y |
| Valid internal links | X/Y | X/Y |

## Critical Issues
[Auto-fixed and remaining broken structural issues]

## Content Issues
[Thin articles, missing sections, contradictions]

## Coverage Gaps
[Orphan summaries, shallow topics, disconnected concepts]

## Open TODOs
[Every TODO: found, with source article]

## Freshness Concerns
[Articles flagged for potential refresh]

## Recommended Next Actions
[5-10 prioritized concrete actions]
```

## Step 8: New article candidates
List 3-5 article or research candidates with a one-sentence rationale each.

# Skill: Wiki Health Check

> **How to use:** Copy this file to your second brain's `.claude/commands/lint.md`
> Then run `/lint` in Claude Code from your second brain folder.
> Optional: `/lint deep` to run contradiction detection (slower but more thorough).

---

Perform a health check on the wiki. Process articles in parallel where possible.

## Step 1: Inventory
- Count all files in `wiki/summaries/`, `wiki/concepts/`, `wiki/queries/`, `wiki/briefings/`
- Read `wiki/_index.md`

## Step 2: Structural checks
For every article in `wiki/` (excluding `_index.md`):

- [ ] Has a first paragraph (summary)?
- [ ] Has a `## Sources` section?
- [ ] Has a `## Related Articles` section?
- [ ] All `[[internal links]]` point to files that exist? (check each link)

**Auto-fix:** If `## Sources` or `## Related Articles` is missing, add it (empty) automatically.
**Do NOT auto-fix** content issues — just flag them.

## Step 3: Content checks (concept articles only)
- [ ] Cites at least 2 sources?
- [ ] Has a `## Key Insights` section?
- [ ] Has any `TODO:` markers? (collect all of them)
- [ ] Is the article substantively thin (< 200 words)? Flag as "needs enrichment"

## Step 4: Coverage checks (wiki-wide)
- Which summaries have NO corresponding concept article?  → "orphan summaries"
- Which topics in the index have only 1 article (shallow coverage)?
- Which concept articles are not linked from any other article? → "disconnected concepts"

## Step 5: Contradiction detection (run if `$ARGUMENTS` == "deep")
Compare claims across concept articles. Look specifically for:
- Conflicting statistics or dates
- Contradictory assessments (e.g., one article says "regulatory environment is favorable", another says "regulatory risk is high")
- Different definitions of the same term
Flag any contradictions found with the specific articles and lines involved.

## Step 6: Freshness check
- Note any articles based entirely on sources dated more than 18 months ago
- Flag these as "may need refresh"

## Step 7: Write the health report

Save to `wiki/health-report.md`:

```
# Wiki Health Report — [date]

## Scorecard
| Check | Pass | Fail | Notes |
|-------|------|------|-------|
| Summary paragraph | X/Y | X/Y | |
| Sources section | X/Y | X/Y | Auto-fixed N |
| Related Articles | X/Y | X/Y | Auto-fixed N |
| Internal links valid | X/Y | X/Y | |
| Concept quality | X/Y | X/Y | |

## Critical Issues
[Auto-fixed issues, and any remaining broken links or missing required structure]

## Content Issues
[Thin articles, missing Key Insights, contradictions if deep mode]

## Coverage Gaps
[Orphan summaries, shallow topics, disconnected concepts]

## Open TODOs
[Full list of every TODO: marker found, with source article]

## Freshness Concerns
[Articles flagged for potential refresh]

## Recommended Next Actions
[Prioritized list of 5-10 concrete actions to improve the wiki]
```

## Step 8: Suggest new article candidates

Based on:
- Topics mentioned in multiple summaries but not yet in a concept article
- Open TODOs that point to missing knowledge
- Connections between concepts not yet captured

List 3-5 new article or research candidates with a one-sentence rationale for each.

# Linting: Keeping Your Wiki Healthy

## Why Wikis Degrade Without Maintenance

As your wiki grows, problems accumulate without active maintenance:
- Articles become outdated as new sources contradict them
- Broken links appear when articles are renamed or reorganized
- Coverage becomes uneven — some topics have 10 articles, others just one
- Contradictions emerge between articles written at different times
- TODO markers pile up, never addressed

A human curator would spend hours on this. Claude can do it in minutes.

---

## The Lint Skill

```
/lint
```

From `.claude/skills/lint/SKILL.md`:

```markdown
# Skill: Wiki Health Check

Perform a comprehensive health check on the wiki. 
Process articles in parallel where possible.

## Checks to Run

### Structural checks (every article)
- Has a summary paragraph at the top?
- Has a ## Sources section?
- Has a ## Related Articles section?
- Are all internal [[links]] pointing to files that exist?

### Content checks (concept articles only)
- Does it cite at least 2 sources?
- Does it have a ## Key Insights section?
- Are there any TODO: markers? (collect these)
- Does it contradict claims in other concept articles?

### Coverage checks (wiki-wide)
- Which topics in the index have only 1 article? (coverage gaps)
- Are there summaries with no linked concept article? (orphans)
- Are there concepts not linked from any summary? (disconnected)

### Freshness checks
- Are any articles based only on sources older than 1 year?
- Flag these for potential refresh.

## Output
Write a health report to wiki/health-report.md with:
1. Summary scorecard (X/Y articles pass each check)
2. Critical issues (broken links, missing structure)
3. Content issues (contradictions, thin coverage)
4. Open TODOs (collected from all articles)
5. Recommended next actions (prioritized list of 5-10 things to do)

Also fix critical structural issues (broken links, missing sections) 
automatically if the fix is straightforward.
```

---

## Reading the Health Report

After running `/lint`, open `wiki/health-report.md`. A sample output:

```markdown
# Wiki Health Report — 2024-01-15

## Scorecard
- 23 articles checked
- Structural compliance: 18/23 (78%) ✓
- Content quality: 15/23 (65%) — needs attention
- Cross-linking: 12/23 (52%) — significant gaps

## Critical Issues (fixed automatically)
- Fixed 3 broken internal links in concepts/battery-storage.md
- Added missing Sources section to summaries/article-7-summary.md

## Content Issues
- concepts/regulatory-risk.md contradicts concepts/eu-policy.md on 
  subsidy timelines — needs reconciliation
- summaries/paper-3-summary.md is an orphan — not linked to any concept article
- concepts/grid-infrastructure.md has only 1 source citation

## Open TODOs
- concepts/battery-storage.md: "TODO: Need US regulatory data post-IRA"
- concepts/solar-economics.md: "TODO: Verify cost figures with 2024 data"
- summaries/interview-summary.md: "TODO: Follow up on claim about Chinese supply chain"

## Recommended Next Actions
1. Resolve contradiction between regulatory-risk.md and eu-policy.md
2. Run /compile to connect paper-3-summary.md to a concept article
3. Ingest sources on US energy regulation (covers the IRA TODO)
4. Verify solar cost figures with recent data (web search)
5. Write a concept article on grid infrastructure (only 1 source, low coverage)
```

This is a roadmap. It tells you exactly what to do next.

---

## Imputing Missing Data with Web Search

When the lint report surfaces gaps, you can ask Claude to fill them:

```
The lint report found that concepts/battery-storage.md needs updated 
US regulatory data post-IRA. Use web search to find the current state 
of US battery storage policy and add a new section to the article. 
Note the source URL in the Sources section.
```

Claude will search, read the results, and update the article. Then run `/ingest` on any interesting full articles it found.

---

## Finding Interesting Connections

The linter can also run a creative pass:

```
After the health check, do a connection pass: look for non-obvious 
relationships between concept articles that aren't currently cross-linked. 
For each interesting connection you find, add a sentence explaining 
the relationship and add a cross-link.
```

LLMs are surprisingly good at this. They'll find connections you missed — a theme in your energy research that also appears in your supply chain research, for example.

---

## Suggesting New Research Directions

```
Based on the current state of the wiki and the open TODOs, suggest 
5 specific sources or topics I should research next. For each, explain 
why it would meaningfully improve the wiki.
```

This turns the linter into a research advisor. As your wiki grows, the suggestions get sharper because Claude has more context to reason from.

---

## Linting Cadence

| Wiki size | Lint frequency |
|-----------|---------------|
| < 20 articles | As needed, after major compile |
| 20–50 articles | Monthly |
| 50+ articles | Every 2 weeks |

Consider adding a `/briefing` skill that runs a light lint check + weekly summary and saves it to `wiki/briefings/`. Run it every Monday morning.

---

**Next:** [07 — Going Further: Advanced Patterns](07-going-further.md)

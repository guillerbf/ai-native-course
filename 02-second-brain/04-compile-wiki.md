# Compile: Building the Knowledge Wiki

## Summaries vs Synthesis

Ingesting produces **summaries** — one-to-one representations of your sources. This is useful, but it's not a knowledge base yet.

**Compiling** produces **synthesis** — concept articles that connect ideas across multiple sources, identify patterns, and build the actual wiki.

```
raw/article-1.md  ──→  wiki/summaries/article-1-summary.md
raw/article-2.md  ──→  wiki/summaries/article-2-summary.md
raw/article-3.md  ──→  wiki/summaries/article-3-summary.md
                              │
                    [compile step]
                              │
                              ▼
                  wiki/concepts/battery-storage.md    ← synthesizes all three
                  wiki/concepts/solar-economics.md    ← connects articles 1 & 3
                  wiki/concepts/regulatory-risk.md    ← from articles 2 & 3
```

Concept articles are where your second brain becomes genuinely intelligent — a map of ideas, not just a pile of summaries.

---

## The Compile Skill

```
/compile
```

From `.claude/skills/compile/SKILL.md`:

```markdown
# Skill: Compile Wiki

1. Read wiki/_index.md to understand what's already compiled
2. Read all files in wiki/summaries/
3. Identify recurring themes, concepts, and entities that appear across 
   multiple summaries (look for: technologies, companies, frameworks, 
   debates, metrics, people, events)
4. For each concept that appears in 3+ summaries AND doesn't already 
   have an article in wiki/concepts/:
   a. Write a comprehensive concept article
   b. The article should: define the concept, describe key debates/dimensions,
      cite specific evidence from summaries, show how different sources 
      relate to it, and list open questions
   c. Save to wiki/concepts/[concept-name].md
5. For existing concept articles: check if new summaries add new information.
   If so, update the article and note the update at the bottom.
6. Add cross-links: in each concept article, link to related concepts
7. Update wiki/_index.md with all new/updated concept articles

Report: concepts created, concepts updated, cross-links added.
```

---

## What a Good Concept Article Looks Like

```markdown
# Battery Storage Economics

Battery storage is becoming economically competitive with fossil fuel 
peaker plants in most markets, driven by falling lithium-ion costs and 
increasing grid-scale deployments. This article synthesizes current 
evidence and key debates.

## Current State
[2-3 paragraphs on current state of play, citing specific summaries]

## Key Debates
### Cost trajectory
[Evidence from sources, different views]

### Grid integration challenges
[Evidence from sources]

## Key Insights
- Levelized cost of storage has fallen 89% since 2010 (source: research-paper-summary)
- Regulatory uncertainty remains the primary risk in EU markets (source: q3-report-summary)
- TODO: Need more data on US regulatory landscape post-IRA

## Open Questions
- How does lithium supply chain risk affect long-term cost projections?
- What are the land use implications of utility-scale storage?

## Sources
- [[summaries/research-paper-battery-tech-summary]]
- [[summaries/q3-market-report-summary]]
- [[summaries/article-on-solar-panels-summary]]

## Related Articles
- [[concepts/solar-economics]]
- [[concepts/regulatory-risk]]
- [[concepts/grid-infrastructure]]
```

Note the `TODO:` marker — this flags a gap in knowledge that the lint skill will later surface.

---

## The First Compile

After ingesting 5–10 articles, run your first compile:

```
/compile
```

At this scale, Claude will typically find 3–8 concept candidates. Don't worry if they're not perfect — the compile skill gets better as you run it more and as you refine your `CLAUDE.md`.

**What to look for in the output:**
- Are the concepts genuinely meaningful for your domain?
- Are the cross-links sensible?
- Does the index now look like a coherent knowledge base?

**Refinement:** If Claude is finding the wrong concepts (too granular, too broad, or off-topic), add a section to your `CLAUDE.md`:

```markdown
## Concept Guidelines
Concepts should be at the level of: "market dynamics", "technology category", 
"regulatory framework" — not individual companies or single data points.
Avoid concepts that are too broad (e.g. "technology") or too narrow (e.g. "Tesla Q3 earnings").
```

---

## Compile Cadence

How often to compile? A rough guide:

| Wiki size | Compile frequency |
|-----------|------------------|
| 0–20 summaries | After each batch of 5+ new ingests |
| 20–50 summaries | Weekly |
| 50–200 summaries | After significant new ingests or monthly |

Compiling is additive — it adds and updates, never deletes. You can run it as often as you like.

---

## Watching the Wiki Grow

After a few weeks of ingest + compile cycles, open the Obsidian graph view. You'll see:

- **Dense clusters** around your most-researched concepts
- **Bridges** between topic areas you didn't consciously connect
- **Orphan nodes** — summaries not yet linked to any concept (candidates for next compile)

The graph is a visual representation of your knowledge structure. It will surprise you.

---

## Force-Compiling a Specific Concept

Sometimes you want to go deep on one concept before the full compile threshold:

```
I want you to write a detailed concept article on "regulatory risk in 
European energy markets" even though it might only appear in 2 sources. 
Draw on everything in the wiki that's relevant.
```

Claude will handle this as a targeted compile, and you can ask it to add the article to `wiki/concepts/regulatory-risk-europe.md`.

---

**Next:** [05 — Query: Asking Your Brain Questions](05-query-and-qa.md)

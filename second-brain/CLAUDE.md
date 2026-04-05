# Second Brain: [YOUR TOPIC]

> **Instructions:** Replace every `[bracketed section]` with your own content.
> This file is your standing instructions to Claude. The clearer it is, the better Claude performs.

---

## Purpose

This is a personal knowledge base about **[YOUR DOMAIN]**.

Examples of good domain descriptions:
- "renewable energy investment trends in Europe"
- "competitive intelligence on the B2B SaaS market"
- "health, longevity, and performance research"
- "emerging AI tools and their business applications"

## My Goal

[What are the 2-3 key questions you are trying to answer through this research?]

Example: "I want to understand which battery storage technologies are most 
likely to achieve cost parity with gas peakers by 2030, and what the 
regulatory tailwinds and headwinds look like in the EU."

## My Role

I add source material to `raw/`. I ask questions and review outputs.
I rarely edit `wiki/` directly — that's Claude's domain.

## Your Role (Claude)

You read sources in `raw/`, write and maintain all files in `wiki/`, 
answer my research questions, and improve the wiki over time.

You are the researcher, writer, librarian, and analyst.

---

## Directory Structure

```
second-brain/
├── CLAUDE.md              ← These instructions (read every session)
├── raw/                   ← My source material. READ ONLY — never modify.
│   ├── articles/          ← Web articles, blog posts
│   ├── papers/            ← Research papers, reports
│   └── notes/             ← My own notes, meeting transcripts
└── wiki/                  ← Your domain. Create and maintain everything here.
    ├── _index.md          ← Master index — always keep updated
    ├── concepts/          ← Synthesized concept articles
    ├── summaries/         ← One summary per raw/ source
    ├── queries/           ← Saved answers to research questions
    └── briefings/         ← Periodic digest files
```

## File Naming Conventions

- All wiki filenames: `lowercase-with-hyphens.md`
- Summaries: `wiki/summaries/[source-filename]-summary.md`
- Concept articles: `wiki/concepts/[concept-name].md`
- Query answers: `wiki/queries/[YYYY-MM-DD]-[short-slug].md`
- Briefings: `wiki/briefings/[YYYY-MM-DD].md`

---

## Article Format

Every wiki article must have:

1. **Summary paragraph** at the top — one paragraph, used for quick scanning
2. Well-structured `##` sections
3. A `## Key Insights` section with bullet points
4. A `## Sources` section with links to raw files or URLs
5. A `## Related Articles` section with `[[wiki/path]]` links

## Index Format (`wiki/_index.md`)

```markdown
# Wiki Index

Last updated: [date]

## Concepts
- [[concepts/concept-name]] — one sentence description

## Summaries
- [[summaries/source-summary]] — one sentence description

## Queries
- [[queries/date-slug]] — the question asked

## Briefings
- [[briefings/date]] — brief description
```

Update `_index.md` every time you add or significantly change an article.

---

## Important Rules

1. **Never delete or modify files in `raw/`** — they are the source of truth
2. **Always update `_index.md`** after adding content
3. **Use `TODO:`** to mark open questions or gaps in knowledge
4. **Add cross-links** whenever you notice articles relate to each other
5. **Cite sources** — every claim in a concept article should trace to a summary

---

## Concept Guidelines

[Optional: describe what level of concept granularity you want]

Example: "Concepts should be at the level of market dynamics, technology 
categories, or strategic frameworks — not individual companies or events. 
A concept should be something that could have a Wikipedia article about it."

---

## Domain Context

[Optional: 2-3 sentences about your specific perspective and what you care about most]

Example: "I am evaluating this space from the perspective of a growth equity 
investor with a 5-7 year horizon. I care most about: total addressable market, 
technology differentiation, regulatory risk, and management team quality. 
I am less interested in early-stage science and more interested in 
commercially viable applications."

# The Second Brain: Concept and Vision

## What We're Building

A **second brain** is a personal knowledge base where an LLM does most of the work: ingesting sources, writing articles, maintaining links, answering questions, and continuously improving itself.

You are the curator. Claude is the researcher, writer, and librarian.

```
YOU                          CLAUDE
──────                       ──────
Drop in sources         →    Reads, summarizes, categorizes
Ask questions           →    Researches across all content, answers
Give it time            →    Maintains index, finds connections, improves articles
Review outputs          →    Incorporates your feedback
```

The result grows smarter over time. Your explorations get filed back in. The wiki learns from its own queries.

---

## Why This Is Different From Search or RAG

You might wonder: why not just search the web? Or use a Retrieval-Augmented Generation (RAG) system?

**vs. Web Search:**
- Web search gives you raw links. Your second brain gives you synthesized knowledge tailored to *your* context and research history
- Your second brain remembers what you've already learned and builds on it

**vs. RAG systems:**
- RAG retrieves chunks of text and feeds them to an LLM. This works but is brittle — relevance depends on embedding similarity, not understanding
- Your second brain uses an LLM-maintained index and article structure. Claude reads the index, identifies what's relevant, and reads full articles — more like a smart researcher than a search engine
- At the scales that matter for one person (~100–500 articles), full-article reading beats chunked retrieval

**vs. Note-taking tools (Notion, Roam, etc.):**
- You write those. Claude writes this.
- Your notes reflect what you already know. The second brain reflects everything in your sources, including things you haven't read carefully yet.

---

## The Architecture

```
┌──────────────────────────────────────────────────────┐
│                    second-brain/                     │
│                                                      │
│  raw/                        wiki/                   │
│  ├── articles/               ├── _index.md  ◄──────┐ │
│  │   ├── article-1.md        ├── concepts/  │      │ │
│  │   └── article-2.md        │   ├── topic-a.md    │ │
│  ├── papers/                 │   └── topic-b.md    │ │
│  │   └── paper-1.md          ├── summaries/        │ │
│  └── notes/                  │   ├── article-1.md  │ │
│      └── meeting-notes.md    │   └── paper-1.md    │ │
│                              ├── queries/           │ │
│                              │   └── q-2024-01.md  │ │
│                              └── briefings/        ─┘ │
│                                  └── 2024-01-15.md    │
└──────────────────────────────────────────────────────┘
```

**`raw/`** — Source material. You put things here. Claude reads but never modifies.

**`wiki/`** — Claude's domain. It writes, maintains, and organizes everything here.

**`wiki/_index.md`** — A project-defined master table of contents. One-line summaries of every article. You instruct Claude (via `CLAUDE.md`) to keep this updated — it's a convention for this project, not a Claude Code default.

**`wiki/concepts/`** — Synthesized knowledge: Claude identifies recurring themes across sources and writes concept articles.

**`wiki/summaries/`** — One summary per source document in `raw/`.

**`wiki/queries/`** — Saved answers to research questions you've asked.

**`wiki/briefings/`** — Periodic digest files Claude generates on demand.

---

## The Lifecycle of Knowledge

```
1. INGEST         You drop a source into raw/
                  Claude reads it → writes summary → updates index

2. COMPILE        Claude scans all summaries for common concepts
                  Writes or updates concept articles
                  Finds cross-links between articles

3. QUERY          You ask a question
                  Claude reads the index → finds relevant articles → synthesizes answer
                  Saves answer to queries/ and adds to index

4. LINT           Claude audits the wiki
                  Finds inconsistencies, missing data, broken links
                  Suggests new articles, new questions to research

5. ENHANCE        Claude uses web search to fill gaps
                  Imputes missing information
                  Adds new source recommendations
```

These five operations map directly to the skills you'll build in the next lessons.

---

## What You Need

- **Claude Code** — the CLI or desktop app
- **Obsidian** (recommended) — a free markdown editor that renders your wiki beautifully, shows backlinks, supports graph view
- **Obsidian Web Clipper** (optional) — browser extension to clip web articles directly to your `raw/` folder as markdown

No databases, no APIs, no infrastructure. Just files and Claude.

---

## Setting Expectations

| At 10 articles | At 50 articles | At 200+ articles |
|----------------|----------------|------------------|
| A useful reference | A genuine knowledge base | A strategic intelligence system |
| Fast to compile | Needs good indexing | Needs smart querying |
| Single agent fine | Parallel agents help | Teams + linting essential |

Start small. The system works immediately and grows with your investment.

---

**Next:** [02 — Setup: Your Second Brain in 15 Minutes](02-setup.md)

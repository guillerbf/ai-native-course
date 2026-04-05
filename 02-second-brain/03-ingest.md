# Ingest: Feeding Your Brain

## The Ingest Principle

Raw material goes into `raw/`. That's it. You never need to pre-process, structure, or clean it up. Claude handles that.

The only rule: **raw files should be text** (markdown, `.txt`, `.md`). If you have PDFs, convert them to markdown first (many tools do this, including Claude itself if you paste the content).

---

## Sources You Can Ingest

| Source Type | How to Get It into raw/ |
|-------------|------------------------|
| Web articles | Obsidian Web Clipper (browser extension) → saves as .md |
| PDFs / papers | Copy-paste content into a .md file, or use a PDF-to-text tool |
| Your own notes | Write directly as .md and drop in raw/ |
| Meeting notes | Paste transcript or notes into a .md file |
| Reports | Copy key sections into .md files |
| Newsletters | Forward to yourself, copy into .md |
| YouTube transcripts | Paste the auto-generated transcript into .md |

**The Obsidian Web Clipper** is the fastest path for web articles. It converts any webpage to clean markdown with one click. Install it from the Obsidian website.

---

## What a Good Raw File Looks Like

Raw files don't need to be perfect. But a few conventions help Claude process them better:

```markdown
---
title: "Article Title"
source: https://example.com/article
date: 2024-01-15
author: Jane Smith
---

# Article Title

[Full article content here...]
```

The frontmatter (the `---` block at the top) is optional but useful. It gives Claude metadata to cite in summaries.

If you're in a hurry, just paste the content. Even unformatted text works.

---

## The Ingest Skill

Once you have files in `raw/`, you run the ingest skill. Here's what it does:

```
/ingest
```

Under the hood (from `.claude/skills/ingest/SKILL.md`):

```markdown
# Skill: Ingest New Sources

1. List all files in raw/
2. List all files in wiki/summaries/
3. Find files in raw/ that don't have a corresponding summary in wiki/summaries/
4. For each new file (process up to 5 at a time to stay focused):
   a. Read the file carefully
   b. Write a summary article following the wiki article format in CLAUDE.md
   c. Save to wiki/summaries/[filename]-summary.md
   d. Add a line to wiki/_index.md under "## Summaries"
5. Report: how many new files processed, how many already had summaries

After processing, identify any concepts that appear in 2+ new summaries and 
note them at the bottom of your report as "Concept candidates: [list]"
```

---

## Running Your First Ingest

1. Add 3–5 source files to `raw/` (articles, notes, reports on your topic)

2. In Claude Code, run:
```
/ingest
```

3. Claude will process each file and tell you what it created

4. Open Obsidian — you'll see the summaries appear in `wiki/summaries/` and the index updated

**Expected output from Claude:**
```
Processed 4 new files:
- wiki/summaries/article-on-solar-panels-summary.md ✓
- wiki/summaries/q3-market-report-summary.md ✓
- wiki/summaries/interview-transcript-ceo-summary.md ✓
- wiki/summaries/research-paper-battery-tech-summary.md ✓

Updated wiki/_index.md with 4 new entries.

Concept candidates: "battery storage economics", "solar installation costs", 
"regulatory environment"
```

---

## Incremental Ingest

One of the most powerful aspects of this system: **ingest is incremental**.

Run `/ingest` today with 3 articles. Come back next week with 5 more. Run `/ingest` again. It processes only the new files — the ones without summaries — and skips everything already done.

Over weeks and months, your brain grows steadily without any effort from you beyond dropping in sources.

---

## Batch vs Careful Ingest

For large batches (20+ files), consider asking Claude to be more concise:

```
/ingest
Process all new files. For each, write a compact summary (2 paragraphs max). 
Prioritize speed over depth — we can enrich later.
```

For important sources you want deeply analyzed:

```
Carefully ingest raw/this-important-paper.md — I want a detailed 5-section 
summary with a Key Insights section and a list of open questions it raises.
```

The skill is a starting point. You can always override with additional instructions.

---

## Pro Tips

**Pre-tag your sources:** Add a line at the top of raw files: `Tags: market-analysis, europe, 2024`. Claude will pick these up and use them in summaries.

**Annotate while reading:** Add your own comments in raw files prefixed with `[MY NOTE: ...]`. Claude will treat these as your perspective and incorporate them.

**Use subfolders in raw/:** `raw/articles/`, `raw/papers/`, `raw/notes/` — Claude handles these automatically.

---

**Next:** [04 — Compile: Building the Knowledge Wiki](04-compile-wiki.md)

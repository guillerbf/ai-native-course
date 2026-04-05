# Setup: Your Second Brain in 15 Minutes

## What You'll Create

By the end of this lesson, you'll have a fully configured second brain ready to ingest its first sources.

---

## Step 1: Create the Folder Structure (2 minutes)

Create this structure on your computer. You can do it manually or paste this into Claude Code:

```
Create this folder structure:
second-brain/
├── CLAUDE.md
├── raw/
└── wiki/
```

Or run these commands in your terminal:
```bash
mkdir -p second-brain/raw second-brain/wiki
touch second-brain/raw/.gitkeep
```

---

## Step 2: Write Your CLAUDE.md (5 minutes)

This is the most important file. Customize it for your domain.

Copy the template below into `second-brain/CLAUDE.md` and fill in the bracketed sections:

```markdown
# Second Brain: [YOUR TOPIC]

## Purpose
This is a personal knowledge base about [YOUR DOMAIN — e.g. "renewable energy 
investment trends", "competitive intelligence on the SaaS market", "health and 
longevity research"].

## My Role
I (the user) add source material to raw/. I ask questions and review outputs.
I rarely edit wiki/ directly.

## Your Role (Claude)
You read sources, write wiki articles, maintain the index, answer questions, 
and improve the wiki over time. You are the researcher, writer, and librarian.

## Directory Structure
- raw/          Source material. Read only — never modify these files.
- wiki/         Your domain. Create, update, and maintain all files here.
- wiki/_index.md  Master index. Update this every time you add or modify an article.
  
## File Naming Conventions
- All wiki filenames: lowercase-with-hyphens.md
- Summaries: wiki/summaries/[source-filename]-summary.md
- Concept articles: wiki/concepts/[concept-name].md
- Query answers: wiki/queries/[YYYY-MM-DD]-[short-slug].md
- Briefings: wiki/briefings/[YYYY-MM-DD].md

## Article Format
Every wiki article must have:
1. A one-paragraph summary at the top (used for quick scanning)
2. Well-structured H2 sections
3. A ## Key Insights section with bullet points
4. A ## Sources section with links to relevant raw/ files or URLs
5. A ## Related Articles section with links to other wiki articles

## Index Format (wiki/_index.md)
Each entry: `- [[article-path]] — one sentence description`
Grouped by: Concepts | Summaries | Queries | Briefings

## Important Rules
- Never delete files from raw/
- Always update _index.md after adding or significantly changing an article
- If you're unsure where to file something, create a wiki/misc/ folder
- Mark open questions as TODO: in the text so they can be found
- When you find connections between articles, add cross-links

## Domain Context
[OPTIONAL: Add 2-3 sentences about your specific research context. 
What are the key questions you're trying to answer? What's your perspective?
E.g. "I am a fund manager evaluating climate tech investments. I care most 
about market size, regulatory risk, and founder quality indicators."]
```

---

## Step 3: Install Obsidian (optional but recommended, 5 minutes)

> **Note on the index:** The `CLAUDE.md` template tells Claude to maintain a `wiki/_index.md` file. This is a convention defined in `CLAUDE.md` — Claude will create it automatically on first run. It is not a Claude Code default; it is an instruction you give Claude.

1. Download [Obsidian](https://obsidian.md) — free
2. Open it, choose "Open folder as vault"
3. Select your `second-brain/` folder
4. You now have a visual interface for your wiki: backlink panel, graph view, search

**Useful Obsidian plugins to install later:**
- **Dataview** — query your wiki like a database
- **Marp** — render slide presentations from markdown
- **Kanban** — visual task boards

---

## Step 5: Open in Claude Code (1 minute)

```bash
cd second-brain
claude
```

Or open the `second-brain/` folder in the Claude Code desktop app.

Test that it's working:
```
Tell me what this project is set up to do, based on CLAUDE.md.
```

Claude should describe your second brain accurately. If not, refine your `CLAUDE.md`.

---

## Quick Validation Checklist

- [ ] `second-brain/CLAUDE.md` exists and is filled in with your domain
- [ ] `second-brain/raw/` exists (empty is fine)
- [ ] `second-brain/wiki/` exists (Claude will populate it)
- [ ] Claude Code can open the folder
- [ ] Claude correctly describes the project when asked

---

## What's Next

Your second brain is configured and empty. In the next lesson, you'll feed it its first sources.

**Next:** [03 — Ingest: Feeding Your Brain](03-ingest.md)

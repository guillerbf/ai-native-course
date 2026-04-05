# Lesson 1: Markdown Files — Claude's Native Language

## The Key Insight

Claude Code doesn't work with a chat window. It works with **files on your computer**.

This changes everything. Instead of losing conversations, your work accumulates. Instead of copy-pasting outputs, Claude writes directly into your project. Instead of starting fresh each session, Claude reads what's already there.

Markdown (`.md`) files are the foundation because:
- They are plain text — no proprietary format, no app required
- They render beautifully in tools like Obsidian, VS Code, GitHub
- Claude can read and write them as naturally as a human reads a document
- They support headings, links, tables, code blocks, images — enough structure to organize any knowledge

---

## What a Markdown File Looks Like

```markdown
# Article Title

A short summary of what this is about.

## Section One

Regular prose. You can write anything here.

## Section Two

| Column A | Column B |
|----------|----------|
| Value 1  | Value 2  |

## Links

- [[Related Article]]   ← Obsidian-style wikilink
- [External Source](https://example.com)
```

That's it. No code required. Claude reads this, understands the structure, and can update it intelligently.

---

## The Hierarchical Structure

Claude Code projects are organized as a **tree of directories and files**. This mirrors how knowledge itself is organized: from broad categories down to specific details.

```
my-project/
├── CLAUDE.md              ← Instructions for Claude (more on this soon)
├── raw/                   ← Source material you feed in
│   ├── article-1.md
│   └── paper-2.md
└── wiki/                  ← Claude's compiled knowledge
    ├── _index.md          ← Master table of contents
    ├── concepts/
    │   ├── topic-a.md
    │   └── topic-b.md
    └── summaries/
        └── article-1-summary.md
```

**Why this matters for you:** You control the structure. Claude follows it. If you want Claude to put summaries in `wiki/summaries/`, you say so in `CLAUDE.md` and it will.

---

## CLAUDE.md — Your Instructions File

The most important file in any Claude Code project is `CLAUDE.md`. It lives at the root and tells Claude:
- What this project is for
- How it should organize files
- What conventions to follow
- What it should and shouldn't do

Think of it as the standing instructions you'd give a very capable employee on their first day.

**Example CLAUDE.md:**
```markdown
# Project: My Research Knowledge Base

## What This Is
A personal wiki about renewable energy trends. All source material is in raw/. 
The compiled wiki lives in wiki/.

## Conventions
- All wiki articles use lowercase-with-hyphens filenames
- Every article ends with a ## Sources section
- The file wiki/_index.md is always kept up to date with links to all articles
- Images go in wiki/images/

## What NOT to Do
- Do not delete files in raw/
- Do not edit raw/ files — they are source material
```

---

## Hands-On Exercise

1. Create a new folder on your computer called `my-first-brain`
2. Inside it, create a file called `CLAUDE.md` with a description of a topic you care about (your industry, a hobby, a research area)
3. Create a folder called `raw/` and drop one article or document into it as a `.md` file
4. Open the folder in Claude Code and ask: *"Read CLAUDE.md and the file in raw/, then create a wiki/ folder with a summary article."*

---

## Key Takeaways

- Claude works with files, not chat windows — your work persists
- Markdown is the native format: readable by humans and LLMs alike
- Directory structure = knowledge structure: design it intentionally
- `CLAUDE.md` is your instruction set: write it clearly and Claude follows it

---

**Next:** [02 — Context: What Claude Sees](02-context.md)

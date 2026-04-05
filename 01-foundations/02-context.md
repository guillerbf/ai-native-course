# Lesson 2: Context — What Claude Sees When It Works

## The Mental Model

Every time Claude does something for you, it operates within a **context window** — a finite amount of information it can hold in "working memory" at once.

Think of it like a very smart consultant sitting at a desk. The desk has limited space. You can put documents on the desk, and the consultant reads and works with whatever is on the desk. If the desk is full, you have to choose what to keep on it.

Claude Code is intelligent about managing this. But understanding it helps you design better projects.

---

## What Goes Into Context

When Claude Code runs a task, its context typically includes:

```
┌─────────────────────────────────────────────────────┐
│  CLAUDE.md (project instructions)                   │
│  + files you've asked it to read                    │  
│  + your current request                             │
│  + conversation history (in this session)           │
│  + tool outputs (search results, file reads, etc.)  │
└─────────────────────────────────────────────────────┘
              = what Claude "knows" right now
```

The more relevant files you have, and the clearer your `CLAUDE.md`, the better Claude performs — because its context is filled with signal, not noise.

---

## Context and Memory

Claude Code has two kinds of memory. Understanding both helps you design better projects.

### Auto Memory (Built-in)

Claude Code automatically maintains a memory file at `~/.claude/projects/<project>/memory/MEMORY.md`. Claude writes to this autonomously — build commands it discovered, debugging insights, architecture notes, code style preferences. It loads the first part of this file at the start of every session.

You can view and edit it via `/memory` in Claude Code, or turn it off in settings.

### File-Based Memory (You Design It)

For a knowledge base — which is what the second brain is — auto memory isn't enough. Auto memory is shallow notes Claude keeps for itself. What you want is a deep, structured, searchable wiki that *you* can read too.

This is where your file structure matters: **the wiki files are the memory for your domain knowledge.**

| What persists between sessions | What does NOT persist |
|-------------------------------|----------------------|
| Everything written to files | The conversation itself |
| Your CLAUDE.md instructions | Temporary analysis |
| The wiki articles Claude created | What you "told" Claude verbally |
| Auto memory (Claude's own notes) | — |

**Practical implication:** When Claude builds your wiki, the wiki is the memory. Next session, Claude reads the wiki and picks up where it left off — not because it has magic recall, but because the information is in the files.

---

## How Claude Manages Large Projects

For a large knowledge base with hundreds of files, Claude can't read everything at once. It uses strategies to stay efficient:

### 1. Index Files
You can instruct Claude (via `CLAUDE.md`) to maintain an index file that lists all articles with brief summaries. Before diving into details, Claude reads the index to understand what exists — like a table of contents. This is a convention you define for your project, not a Claude Code default.

### 2. Targeted Reading
When you ask a question, Claude reads the index first, identifies the 3–5 most relevant articles, then reads those in full. It doesn't need to read everything to give a good answer.

### 3. Summaries Within Articles
Well-structured wiki articles start with a short summary paragraph. Claude can quickly scan these to decide whether to read deeper.

---

## The Context Hierarchy in Claude Code

Claude Code has a layered system for loading context:

```
CLAUDE.md (root)           ← Always read, global instructions
  └── CLAUDE.md (subfolder) ← Read when working in that folder, local instructions
        └── individual files ← Read on demand
```

You can put a `CLAUDE.md` inside `wiki/concepts/` that gives specific instructions for that subfolder (e.g. "All articles here follow the Zettelkasten format"). Claude layers this on top of the root instructions.

---

## Designing for Context Efficiency

Good project design makes Claude's job easier and your results better:

**Do:**
- Keep `CLAUDE.md` concise and focused
- Define a project-specific index convention and tell Claude to maintain it
- Name files descriptively (`solar-energy-economics.md` not `article-3.md`)
- Write summary paragraphs at the top of every wiki article

**Avoid:**
- Dumping huge unstructured documents into raw/
- Having hundreds of files with no index
- Writing vague or contradictory instructions in CLAUDE.md

---

## Hands-On Exercise

Open a Claude Code session in your `my-first-brain` folder and try this sequence:

1. Ask Claude: *"List all the files in this project and describe what each one contains."*
   → Watch how Claude reads the file structure as context.

2. Ask Claude: *"Based on what you've read, what topics are not yet covered that would be useful to add?"*
   → Claude reasons over its context to generate insight.

3. Close the session, open a new one, and ask the same question again.
   → Notice it reads the files again — context doesn't persist, but files do.

---

## Key Takeaways

- Context window = what's on the desk right now
- Claude Code has built-in auto memory (`~/.claude/projects/<project>/memory/`) for lightweight notes Claude writes itself
- For structured knowledge bases, file-based memory (your wiki) is the right approach — deeper, human-readable, and you control it
- Design your file structure to be context-efficient: indexes, summaries, clear names
- CLAUDE.md is loaded first — make it count

---

**Next:** [03 — Skills: Teaching Claude New Tricks](03-skills.md)

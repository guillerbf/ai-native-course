# Lesson 5: Subagents and Teams — Parallel Intelligence

## The Limitation of a Single Agent

A single agent works sequentially: it does step 1, then step 2, then step 3. For most tasks, this is fine.

But some tasks are naturally parallel:
- Summarizing 20 articles independently (each summary doesn't depend on the others)
- Running a health check on each section of the wiki simultaneously
- Answering a complex question that requires researching 5 different sub-topics at once

For these, a single sequential agent is like having one employee do everything alone when you could have a coordinated team.

---

## Subagents: Parallel Workers

A **subagent** is a specialized Claude instance spawned by a parent agent to handle a specific subtask. The parent coordinates; the subagents execute in parallel.

```
Parent Agent (coordinator)
│
├── Subagent A: "Summarize article-1.md"      ──┐
├── Subagent B: "Summarize article-2.md"      ──┤  all running
├── Subagent C: "Summarize article-3.md"      ──┤  simultaneously
└── Subagent D: "Summarize article-4.md"      ──┘
│
└── [collects all results] → updates index
```

What might take 4 minutes sequentially takes 1 minute with 4 parallel subagents.

---

## Teams of Agents: Specialization

Beyond parallelism, agents can be **specialized**. Different agents are given different instructions, different tools, and different scopes.

For your second brain, a natural team structure:

```
┌─────────────────────────────────────────────────────────────┐
│                     ORCHESTRATOR                            │
│         Reads goals, assigns work, synthesizes results      │
└──────────────┬───────────────┬──────────────┬──────────────┘
               │               │              │
    ┌──────────▼───┐  ┌────────▼────┐  ┌─────▼──────────┐
    │   INGESTER   │  │  COMPILER   │  │    ANALYST     │
    │ Processes    │  │ Writes wiki │  │ Answers queries │
    │ raw sources  │  │ articles    │  │ finds patterns  │
    └──────────────┘  └─────────────┘  └────────────────┘
               │               │              │
    ┌──────────▼───┐  ┌────────▼────┐  ┌─────▼──────────┐
    │    LINTER    │  │  INDEXER    │  │   GENERATOR    │
    │ Health checks│  │ Maintains   │  │ Creates slides, │
    │ consistency  │  │ _index.md   │  │ reports, charts │
    └──────────────┘  └─────────────┘  └────────────────┘
```

Each specialist is optimized for its role. The orchestrator delegates intelligently.

---

## How This Works in Claude Code

In Claude Code, the `Agent` tool lets Claude spawn subagents. When you ask for a large task, Claude can internally decide: *"This is faster if I split it."*

You can also explicitly ask for parallel execution:

```
Compile the wiki from all 15 articles in raw/. Process them in parallel — 
don't wait for one summary to finish before starting the next.
```

Or design your skills to use parallel subagents:

```markdown
# Skill: Parallel Ingest

For each file in raw/ that needs processing:
- Spawn a subagent to handle each file independently
- Each subagent: reads the file, writes the summary, notes key concepts
- Once all subagents complete, run the indexer to update _index.md
```

---

## Specialized Agents via CLAUDE.md

You can create specialized agents by giving them different `CLAUDE.md` files. In a multi-folder project:

```
second-brain/
├── CLAUDE.md              ← Master instructions (orchestrator behavior)
├── raw/
│   └── CLAUDE.md          ← "You are the ingester. Your only job is..."
├── wiki/
│   └── CLAUDE.md          ← "You are the compiler. Follow these article formats..."
└── queries/
    └── CLAUDE.md          ← "You are the analyst. When answering questions..."
```

Each subfolder has its own instruction set. When Claude works in that folder, it adopts that specialized role.

---

## Practical Example: Complex Research Query

You ask: *"What are the strategic implications of recent developments across all my research areas?"*

A team approach:
1. **Orchestrator** reads the question, identifies 5 research domains in the wiki
2. **5 subagents** each research one domain in parallel, producing a mini-report
3. **Orchestrator** reads all 5 mini-reports and synthesizes a strategic overview
4. **Generator subagent** formats the overview as a slide deck (Marp format)
5. **Indexer subagent** files the report back into the wiki

This kind of multi-agent workflow transforms a 30-minute manual analysis into a 2-minute automated one.

---

## When to Use Subagents vs a Single Agent

| Use a single agent when... | Use subagents when... |
|---------------------------|----------------------|
| Tasks must happen in sequence | Tasks are independent of each other |
| Volume is small (< 5 items) | Volume is large (10+ items) |
| Consistency of style is critical | Speed matters more than uniformity |
| You want to review each step | You trust the process and want throughput |

---

## Hands-On Exercise

Once your wiki has at least 10 articles, try this:

1. Ask Claude to run a **parallel health check**:
```
Run a health check on the wiki in parallel. For each article in wiki/, 
spawn a check that: verifies the article has a summary paragraph, 
has a Sources section, and has no broken internal links. 
Compile all findings into wiki/health-report.md.
```

2. Observe how Claude handles the parallelism

3. Review `wiki/health-report.md` — this is what a team produced for you

---

## Module Summary: The Five Concepts

| Concept | What It Is | Your Role |
|---------|-----------|-----------|
| **Markdown files** | Claude's working medium | Design structure, write CLAUDE.md |
| **Context** | What Claude sees at runtime | Keep it clean, indexed, summarized |
| **Skills** | Reusable workflows | Define once, invoke repeatedly |
| **Agents** | Autonomous task execution | Set goals, review outputs |
| **Subagents / Teams** | Parallel specialized execution | Design team structure, enable parallelism |

These five concepts are the architecture of AI-native work. You now have the mental models to use them.

---

**Next Module:** [02 — Building Your Second Brain](../02-second-brain/01-concept.md)

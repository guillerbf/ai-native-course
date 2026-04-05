# Lesson 4: Agents — Claude Working Autonomously

## From Assistant to Agent

In a standard chat, you and Claude go back and forth: you ask, it answers, you react, it adjusts. You are always in the loop.

An **agent** is different. You give Claude a goal, and it figures out the steps, executes them in sequence, reads the results, makes decisions, and continues — all without waiting for you after each step.

```
Standard chat:          You → Claude → You → Claude → You → ...

Agent:                  You → Claude → [reads file] → [writes file] → [searches] → [updates index] → Done ✓
```

The agent loop: think → act → observe result → think again → act again → ... → goal achieved.

---

## What Makes an Agent Powerful

Agents have **tools** — capabilities beyond just generating text:

| Tool | What It Does |
|------|-------------|
| Read file | Reads any file in your project |
| Write file | Creates or overwrites a file |
| Edit file | Makes targeted edits to existing content |
| Search files | Finds files matching a pattern or containing a keyword |
| Run command | Executes a terminal command |
| Web search | Searches the internet |
| Web fetch | Reads a specific URL |

When Claude acts as an agent on your wiki, a single request like *"compile the wiki from all new sources"* might trigger 30+ tool calls internally — reading files, comparing timestamps, writing articles, updating the index — all autonomously.

---

## The Agentic Mindset: Goals, Not Steps

When you work with agents, **describe the goal, not the procedure.**

| Procedural (don't do this) | Goal-oriented (do this) |
|---------------------------|------------------------|
| "Read raw/article1.md, then write a summary, then add it to the index" | "Make sure all files in raw/ have summaries in the wiki" |
| "Open the index, find broken links, fix them one by one" | "Audit the wiki for broken links and fix them" |
| "Check each article for TODO markers and report them" | "Give me a list of open research questions in the wiki" |

The agent will figure out the procedure. Your job is to be clear about the outcome.

---

## How Claude Code's Agent Loop Works

When Claude Code operates as an agent:

```
1. Read CLAUDE.md (understand the project)
2. Understand the goal you've stated
3. Make a plan (sometimes shown to you, sometimes implicit)
4. Execute step 1 → observe result
5. Decide next step based on result
6. Execute step 2 → observe result
7. ... repeat ...
8. Recognize goal is achieved
9. Report back to you
```

Claude can handle branches: if a file doesn't exist, create it. If a file already has a summary, skip it. If a search returns nothing, try a different approach. This is genuine autonomous problem-solving.

---

## When to Let the Agent Run vs When to Stay in the Loop

Not every task should run fully autonomously. Use your judgment:

**Let it run (low risk, reversible):**
- Compiling summaries from sources
- Updating the index
- Answering a research question and saving the output
- Linting/health-checking the wiki

**Stay in the loop (review before continuing):**
- Restructuring your entire wiki (could move things you want to find)
- Deleting or archiving content
- Publishing or sharing outputs externally

**Pro tip:** For large autonomous tasks, ask Claude to first describe its plan before executing. You approve the plan, then let it run.

```
"Before making any changes, describe exactly what you plan to do to compile the wiki."
```

---

## Agents Use Memory Through Files

Remember from Lesson 2: the files are the memory. Agents lean on this heavily.

A well-designed agent workflow leaves **artifacts** at each step:
- Reads source → writes summary (artifact)
- Writes summary → updates index (artifact)
- Detects gap → creates TODO entry (artifact)

Next session, the agent reads these artifacts to understand the current state and continues from there. This is how a solo agent can manage a knowledge base that grows over months without losing track.

---

## Hands-On Exercise

In your `my-first-brain` folder, try an extended autonomous task:

1. Add 3–5 articles to your `raw/` folder (copy-paste any articles you find interesting as `.md` files)

2. Give Claude this goal-oriented instruction:
```
Compile the wiki. For every file in raw/ that doesn't yet have a 
summary in wiki/summaries/, create one. Then update wiki/_index.md 
to include all summaries with a one-line description. Finally, 
identify 3 concepts that appear across multiple sources and write 
a concept article for each in wiki/concepts/.
```

3. Watch how Claude executes this without asking you for each step

4. When it's done, review the output — does it match your intent?

5. Refine your `CLAUDE.md` based on anything that wasn't quite right

---

## Key Takeaways

- Agents execute multi-step workflows autonomously using tools
- Describe goals, not procedures — Claude figures out the steps
- The agent loop: think → act → observe → think → act → ...
- Files are the agent's persistent memory between sessions
- Balance autonomy with oversight: let it run on low-risk tasks, review plans for high-impact ones

---

**Next:** [05 — Subagents and Teams: Parallelizing Work](05-subagents-and-teams.md)

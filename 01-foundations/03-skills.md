# Lesson 3: Skills — Teaching Claude Repeatable Behaviors

## What Is a Skill?

A **skill** is a named, reusable prompt stored as a markdown file that Claude can invoke on demand.

Instead of typing the same complex instructions every time ("read the index, find gaps, write a new article, update the index, check for broken links..."), you write it once as a skill and invoke it with a slash command:

```
/compile
```

That's it. Claude reads the skill file, follows the instructions precisely, and executes the full workflow.

---

## The Anatomy of a Skill File

Skills live in a `.claude/commands/` folder in your project (or globally in `~/.claude/commands/`):

```
my-project/
├── CLAUDE.md
└── .claude/
    └── commands/
        ├── ingest.md      ← /ingest skill
        ├── compile.md     ← /compile skill
        ├── query.md       ← /query skill
        └── lint.md        ← /lint skill
```

A skill file is just a markdown file with instructions. Here's a simple example:

```markdown
# Skill: Daily Briefing

Read the file wiki/_index.md and the last 5 files modified in wiki/.
Then write a short briefing (one paragraph) summarizing:
- What topics have been recently updated
- What questions are still open (look for TODO markers)
- One recommendation for what to research next

Save the briefing to wiki/briefings/YYYY-MM-DD.md using today's date.
```

Save this as `.claude/commands/briefing.md` and you can run `/briefing` any time.

---

## Why Skills Matter for Business People

Skills are how you **encode your workflows** into the system.

Every business has repetitive knowledge processes:
- Summarizing a new report and filing it
- Checking if a new development contradicts existing knowledge
- Generating a weekly digest of what's been learned
- Producing a slide deck from research

Without skills, you describe these processes ad-hoc every time. With skills, you define them once and they run reliably, consistently, every time.

**Skills are your institutional memory for how work gets done.**

---

## Skills Can Use Arguments

Skills can accept dynamic inputs using the `$ARGUMENTS` placeholder:

```markdown
# Skill: Research Question

The user wants to research: $ARGUMENTS

1. Search the wiki index for any existing coverage of this topic
2. Identify the 3 most relevant existing articles
3. Read those articles in full
4. Write a comprehensive answer using only the wiki content
5. Note any gaps where more research is needed
6. Save the answer to wiki/queries/[slug-of-question].md
```

Invoke it as:
```
/query What are the main risks in the solar energy market?
```

Claude receives the question as `$ARGUMENTS` and runs the full research workflow.

---

## Project Skills vs Global Skills

| Location | Scope | Use Case |
|----------|-------|----------|
| `.claude/commands/` in your project | This project only | Domain-specific workflows (compile wiki, ingest source) |
| `~/.claude/commands/` on your machine | All projects | General-purpose tasks (daily briefing, code review) |

For your second brain, all skills live in the project — they are tuned to your specific wiki structure and conventions.

---

## The Skill Development Loop

Skills improve over time. The workflow is:

1. **Do it manually** — ask Claude ad-hoc once or twice
2. **Notice the pattern** — you keep asking for the same thing
3. **Write the skill** — capture the instructions in `.claude/commands/`
4. **Refine** — run it, see what's off, edit the skill file
5. **Trust it** — the skill is now part of your workflow

This is how professionals using Claude Code accumulate leverage over time. Your library of skills is a competitive advantage.

---

## Hands-On Exercise

In your `my-first-brain` folder:

1. Create the directory `.claude/commands/`

2. Create `.claude/commands/summarize.md` with these contents:
```markdown
# Skill: Summarize New Source

Look at the files in raw/ that do NOT yet have a corresponding file in wiki/summaries/.
For each new file found:
1. Read the file
2. Write a 3-paragraph summary: what it is, key insights, relevance to the project
3. Save it to wiki/summaries/[filename]-summary.md
4. Add a line to wiki/_index.md linking to the new summary

Report back with how many new files were processed.
```

3. Run `/summarize` in Claude Code

4. Add another article to `raw/` and run `/summarize` again — only the new file should be processed

---

## Key Takeaways

- A skill is a saved prompt that runs a repeatable workflow
- Skills live in `.claude/commands/` as markdown files
- Invoke with `/skill-name` or `/skill-name [arguments]`
- Skills encode your processes — they are institutional memory
- Build your skill library incrementally as patterns emerge

---

**Next:** [04 — Agents: Claude Working Autonomously](04-agents.md)

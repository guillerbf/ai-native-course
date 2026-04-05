# Going Further: Advanced Patterns

## You Have a Working System — Now Extend It

At this point you have a second brain that ingests, compiles, queries, and self-maintains. This final lesson covers advanced patterns for business professionals who want to push it further.

---

## Pattern 1: Multiple Second Brains

You don't have to keep everything in one wiki. Separate second brains work better for separate domains.

```
~/knowledge/
├── competitive-intelligence/   ← market research, competitor analysis
├── technology-radar/           ← emerging tech tracking
├── deal-pipeline/              ← investment or sales research
└── personal-development/       ← books, courses, ideas
```

Each has its own `CLAUDE.md`, its own concept vocabulary, its own query style. Claude operates in each one independently.

**When to separate vs combine:** Separate when the domains don't interact much. Combine when cross-domain connections are valuable (e.g. tech and market research often belong together).

---

## Pattern 2: Team Knowledge Bases

The second brain pattern scales to teams.

Instead of one person's raw/ folder, the whole team contributes:
- Sales drops call notes into `raw/calls/`
- Analysts drop research into `raw/research/`
- Leadership drops strategy documents into `raw/strategy/`

Claude compiles a shared wiki that everyone can query. The team's collective knowledge becomes accessible to everyone instantly.

**Git is perfect for this.** Each person commits new files to `raw/`, and the compile/lint skills run on a schedule or on commit.

---

## Pattern 3: Automated Briefings

Set up a `/briefing` skill and run it on a schedule:

```markdown
# Skill: Weekly Briefing

Generate a weekly intelligence briefing:
1. Check what was added to raw/ in the last 7 days
2. Check which wiki articles were updated in the last 7 days
3. Check wiki/queries/ for any new research done this week
4. Write a 1-page executive briefing:
   - What's new this week
   - Key insights from new content
   - Open questions surfaced this week
   - Recommended focus for next week
5. Save to wiki/briefings/[YYYY-MM-DD]-weekly.md
```

Run this every Monday morning. In Obsidian, the briefings folder becomes a journal of your intellectual progress.

---

## Pattern 4: Output as Deliverables

Your wiki isn't just for personal use — it can generate business deliverables:

**Board presentation:**
```
Based on the wiki, generate a 10-slide board presentation on the state 
of our competitive landscape. Use Marp format. Save to wiki/outputs/board-deck-[date].md
```

**Investment memo:**
```
Write a 2-page investment memo on [Company/Market] using everything 
in the wiki. Format: Executive Summary, Market Analysis, Risks, 
Recommendation. Save to wiki/outputs/investment-memo-[topic]-[date].md
```

**Due diligence checklist:**
```
Based on the wiki's coverage of [topic], generate a due diligence 
checklist: what do we know, what should we verify, what are the 
red flags to investigate?
```

These outputs are saved back into the wiki, so they become part of the knowledge base too.

---

## Pattern 5: Comparative Research

When evaluating options (vendors, investments, strategies, candidates), structured comparison is powerful:

```
I'm evaluating 3 battery storage companies: [A], [B], [C].
For each company, check if there's anything in the wiki, then 
use web search to fill gaps. Write a comparison table on: 
technology approach, market traction, management team, 
financial health, regulatory risk. Save to wiki/queries/vendor-comparison-[date].md
```

---

## Pattern 6: The Linter as Research Advisor

As your wiki matures, the linter becomes a research strategist:

```
Looking at the full wiki, what are the 3 most important questions 
we haven't answered yet? For each question: why does it matter, 
what sources might answer it, and what's the best way to find those sources?
```

This is Claude reasoning over months of accumulated research to give you a prioritized research agenda. Better than any research management tool.

---

## Pattern 7: Synthetic Data and Personas

Advanced: once your wiki is large enough, you can create synthetic personas:

```
Based on the competitive intelligence wiki, write responses to these 
questions as if you were our main competitor's head of strategy. 
What are they likely thinking about? What are their priorities? 
Where are they vulnerable?
```

This kind of adversarial or persona-based analysis is only possible when your wiki is rich enough to support it.

---

## What Makes a Great Second Brain

After several months of use, the highest-leverage habits are:

1. **Ingest consistently** — drop something in every few days. Volume matters.
2. **Query often** — each query enriches the wiki
3. **Trust the lint** — fix issues when surfaced, don't ignore the report
4. **Refine CLAUDE.md** — as you learn what you want, update the instructions
5. **Add your perspective** — annotate raw files with `[MY NOTE: ...]`, Claude will use it

The wiki reflects the quality of your curation. But you'll find that even modest curation — regularly dropping in articles — produces a knowledge base far richer than you could maintain manually.

---

## The Bigger Picture

You've built a system where:
- Knowledge accumulates rather than evaporates
- Research compounds rather than restarting each time
- Questions get answered by your own curated sources, not random web results
- The LLM's intelligence is applied to *your* specific domain knowledge

This is the early shape of a fundamental change in how knowledge work gets done. The second brain is not a productivity hack — it's a different model for how professionals handle information.

You're now equipped to build it and grow it. Start small, use it regularly, and watch it become indispensable.

---

## Course Complete

You've covered:
- [x] Markdown files and project structure
- [x] Context and how Claude uses it
- [x] Skills for repeatable workflows
- [x] Agents for autonomous execution
- [x] Subagents and teams for parallel work
- [x] Building and running your second brain
- [x] Advanced patterns for professional use

**Your next step:** Go to `../second-brain/` — it's a ready-to-use starter template. Customize the `CLAUDE.md`, add your first sources, and run `/ingest`.

The skills are in `../03-skills/`. Read them to understand what they do, then copy them into your second brain's `.claude/commands/` folder.

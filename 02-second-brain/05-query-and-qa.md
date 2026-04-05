# Query: Asking Your Brain Questions

## This Is Where It Gets Interesting

Once your wiki has 20+ articles, you can start asking it complex questions — and getting answers that reflect the full depth of your research, synthesized in seconds.

This is qualitatively different from searching the web or asking a generic LLM. The answers come from *your* curated sources, reflect *your* domain expertise, and build on *your* accumulated knowledge.

---

## The Query Skill

```
/query What are the main investment risks in European battery storage?
```

From `.claude/commands/query.md`:

```markdown
# Skill: Research Query

Question: $ARGUMENTS

1. Read wiki/_index.md to understand the full scope of the wiki
2. Identify the 5 most relevant articles (concepts + summaries) for this question
3. Read those articles in full
4. If they reference other articles that seem relevant, read those too
5. Synthesize a comprehensive answer:
   - Lead with a direct answer to the question
   - Support with specific evidence from the wiki
   - Note where sources agree and where they conflict
   - Flag any important gaps in the current wiki coverage
   - Suggest 2-3 follow-up questions that would deepen understanding
6. Save the answer to wiki/queries/[YYYY-MM-DD]-[short-slug].md
7. Add the query to wiki/_index.md under ## Queries

Format the answer as a proper markdown article, not a chat response.
```

---

## Types of Questions You Can Ask

**Factual:**
```
/query What is the current levelized cost of battery storage per MWh?
```

**Comparative:**
```
/query How do European and US regulatory approaches to energy storage differ?
```

**Strategic:**
```
/query What are the 3 biggest risks to a solar + storage investment thesis?
```

**Synthesis:**
```
/query What are the most surprising or counterintuitive findings across all my research?
```

**Gaps:**
```
/query What topics are most underrepresented in my current wiki that I should research next?
```

**Connections:**
```
/query Are there any companies or technologies that appear across multiple 
research areas in ways I might not have noticed?
```

---

## The Query Compounds Over Time

Here's the hidden power: **your queries become part of the wiki.**

When you save a query answer to `wiki/queries/`, it becomes another article in the knowledge base. The next query can draw on it. Your thinking compounds.

Practical example:
- Week 1: You ask about investment risks → answer saved to `wiki/queries/`
- Week 3: You ingest 5 new sources and recompile
- Week 5: You ask a strategic question → Claude reads your previous query AND the new concepts → gives a richer, more nuanced answer that builds on your prior work

Your past thinking doesn't disappear. It amplifies future thinking.

---

## Complex Multi-Part Queries

For big questions, give Claude the full scope:

```
I need to prepare for a board presentation on whether we should enter 
the European battery storage market. Based on everything in the wiki:

1. Write a market overview (1 page)
2. List the top 5 risks with supporting evidence
3. List the top 3 opportunities
4. Identify what we still don't know (gaps)
5. Recommend 3 specific questions to answer before committing

Save each section as a separate file in wiki/queries/board-prep/ and 
create an index file that links them all.
```

This is a multi-agent task. Claude will spawn parallel subagents for sections 1–4 and then synthesize in step 5.

---

## Output Formats

Query answers don't have to be prose. Tell Claude how you want the output:

**Slide deck (Marp format):**
```
/query What is the investment case for battery storage?
Format the answer as a Marp slide presentation. Save to wiki/queries/investment-case-slides.md
```

**Table:**
```
/query Compare the risk profiles of the 5 main European energy markets.
Format as a comparison table.
```

**Executive summary:**
```
/query Summarize the state of battery storage in under 300 words for a 
non-technical executive.
```

**Visual diagram description:**
```
/query Draw a map of how the main concepts in my wiki relate to each other.
Describe it as a mermaid diagram.
```

---

## When Claude Doesn't Know the Answer

Sometimes Claude will tell you: *"Based on the current wiki, I can't fully answer this — here's what I know and what's missing."*

This is valuable. It tells you exactly what to research next. The gap itself is actionable intelligence.

You can then:
1. Go find the missing sources and ingest them
2. Ask Claude to search the web for the missing information: `Use web search to fill in the gap on [topic]`
3. Note it as a TODO in the relevant concept article

---

## Saving Queries Back Into the Wiki

Always save important query answers. Over time, your `wiki/queries/` folder becomes a rich collection of your analytical work — a portfolio of thinking.

In Obsidian, you can see how query articles link back to concept articles and summaries. Your analysis is grounded in evidence.

---

**Next:** [06 — Linting: Keeping Your Wiki Healthy](06-linting-and-health.md)

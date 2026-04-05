# Skill: Research Query

> **How to use:** Copy this file to your second brain's `.claude/commands/query.md`
> Then run `/query [your question]` in Claude Code from your second brain folder.

---

Research question: **$ARGUMENTS**

## Step 1: Understand the scope
Read `wiki/_index.md` in full to understand what knowledge is available.

## Step 2: Identify relevant content
Based on the question and the index, identify:
- The 3-7 most relevant concept articles
- The 2-5 most relevant summaries
- Any previous query answers in `wiki/queries/` that are related

Read all identified articles in full.

## Step 3: Read deeper if needed
If any of the articles you read reference other articles that seem highly relevant, read those too. Follow the thread but stay focused on the question.

## Step 4: Synthesize the answer

Write a comprehensive answer with this structure:

```
# [Short descriptive title for this query]

*Query date: [today's date]*
*Original question: [the question as asked]*

## Answer

[Lead with a direct, clear answer in 2-3 sentences. Don't bury the lede.]

## Analysis

[Detailed analysis. Cite specific evidence from the wiki. 
Use subheadings if the answer has multiple dimensions.]

## Evidence

[Key facts, data, and quotes from the wiki that support the answer. 
Note which articles each piece of evidence comes from.]

## Caveats and Uncertainties

[Where the evidence is thin, conflicting, or outdated. Be honest about limitations.]

## Knowledge Gaps

[What would you need to know to give a more complete answer?
Be specific — what sources or research would fill the gaps?]

## Follow-up Questions

[2-3 questions that naturally arise from this answer and would be valuable to research]

## Sources Used
- [[concepts/article-name]]
- [[summaries/source-name]]
[List all wiki articles that informed this answer]
```

## Step 5: Save and index
- Save the answer to `wiki/queries/[YYYY-MM-DD]-[short-slug].md`
  where short-slug is 3-5 words from the question, hyphenated
- Add to `wiki/_index.md` under `## Queries`:
  `- [[queries/filename]] — [the question, summarized in one line]`

## Step 6: Enrich the wiki (if appropriate)
If the query revealed significant insights or new connections that aren't already captured in concept articles, note them at the end of your response so they can be incorporated in the next `/compile` run.

# Skill: Compile Wiki

> **How to use:** Copy this file to your second brain's `.claude/skills/compile/SKILL.md`
> Then run `/compile` in Claude Code from your second brain folder.
> Optional: `/compile [concept name]` to force-compile a specific concept.

---

Your goal is to synthesize knowledge from summaries into concept articles.

## Step 1: Survey the current state
- Read `wiki/_index.md` in full
- List all files in `wiki/summaries/`
- List all files in `wiki/concepts/`

## Step 2: Identify concepts to write or update

If `$ARGUMENTS` is provided, write/update a concept article on that specific topic.

Otherwise, find concepts that:
- Appear in **3 or more summaries** AND
- Don't yet have a concept article in `wiki/concepts/`

Also check: existing concept articles that should be **updated** because new summaries contain relevant information not yet reflected in them.

## Step 3: For each new concept article

Write a comprehensive article:

```
# [Concept Name]

[One-paragraph synthesis: what this concept is, why it matters in the 
context of this wiki's domain, current state of knowledge]

## Definition and Scope
[Clear definition, scope boundaries — what's in and out of this concept]

## Current State
[What we know from the sources. Cite specific summaries.]

## Key Debates and Tensions
[Where sources agree, where they differ. Be specific about the disagreement.]

## Key Insights
- [Bullet points of the most important analytical conclusions]
- [Focus on non-obvious insights, not just facts]

## Data and Evidence
[Key numbers, studies, or findings that anchor the concept]

## Open Questions
- [Questions the current sources can't answer]
- TODO: [specific gaps to fill]

## Sources
- [[summaries/source1-summary]]
- [[summaries/source2-summary]]
[Link to every summary that informed this article]

## Related Articles
- [[concepts/related-concept-1]]
- [[concepts/related-concept-2]]
[Link to related concept articles]
```

Save to `wiki/concepts/[concept-name].md` (lowercase-hyphenated).

## Step 4: Update existing concept articles

For each concept article that has new relevant information from new summaries:
- Add the new information to the appropriate section
- Add the new source to the ## Sources section
- Add a note at the bottom: `*Updated [date]: added information from [source]*`
- Add any new cross-links to ## Related Articles

## Step 5: Add cross-links between concept articles

Look at all concept articles. For each pair of concepts that relate to each other but don't yet link to each other, add the cross-link in both directions.

## Step 6: Update the index

Add all new concept articles to `wiki/_index.md` under `## Concepts`:
`- [[concepts/concept-name]] — [one sentence description]`

## Report

Provide:
- Concepts created (with article names)
- Concepts updated (with what was added)
- Cross-links added
- Orphaned summaries (summaries not yet connected to any concept — flag these)

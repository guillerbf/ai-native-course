# Skill: Compile Wiki

Your goal is to synthesize summaries into concept articles.

## Step 1: Survey
- Read `wiki/_index.md`
- List all files in `wiki/summaries/` and `wiki/concepts/`

## Step 2: Identify concepts to write or update

If `$ARGUMENTS` is provided, write/update a concept article on that specific topic.

Otherwise find concepts that:
- Appear in **3+ summaries** AND
- Don't yet have an article in `wiki/concepts/`

Also check: existing concept articles that should be updated because new summaries add relevant information.

## Step 3: For each new concept article

```
# [Concept Name]

[One-paragraph synthesis: what this is, why it matters, current state of knowledge]

## Definition and Scope
[Clear definition and boundaries]

## Current State
[What the sources show. Cite specific summaries.]

## Key Debates and Tensions
[Where sources agree vs. differ]

## Key Insights
- [Non-obvious analytical conclusions]

## Data and Evidence
[Key numbers, findings that anchor the concept]

## Open Questions
- [Questions current sources can't answer]
- TODO: [specific gaps to fill]

## Sources
- [[summaries/source1-summary]]
- [[summaries/source2-summary]]

## Related Articles
- [[concepts/related-concept]]
```

Save to `wiki/concepts/[concept-name].md`.

## Step 4: Update existing concept articles

Add new information from new summaries. Append:
`*Updated [date]: added information from [source]*`

## Step 5: Add cross-links

For each pair of concept articles that relate but don't yet link to each other, add the cross-link in both directions.

## Step 6: Update the index

Add new concept articles to `wiki/_index.md` under `## Concepts`.

## Report
- Concepts created
- Concepts updated
- Cross-links added
- Orphaned summaries (not connected to any concept)

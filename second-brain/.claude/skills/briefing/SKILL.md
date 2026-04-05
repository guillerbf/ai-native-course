# Skill: Weekly Briefing

Generate a weekly intelligence briefing for the wiki.

## Step 1: Gather recent activity
- List files in `raw/` modified or created in the last 7 days
- List files in `wiki/` modified or created in the last 7 days
- Check `wiki/queries/` for any new query answers this week

## Step 2: Read recent content
Read any new summaries and updated concept articles from this week.
Skim the index to see the overall shape of the wiki.

## Step 3: Write the briefing

```
# Weekly Briefing — [date]

## This Week in the Wiki
[2-3 sentences: what was added, what was updated, how many new sources]

## Key Developments
[3-5 bullet points of the most important new information or insights 
from sources ingested this week]

## Emerging Themes
[Any patterns or concepts that are starting to crystallize from recent 
additions — what seems to be building toward a concept article?]

## Open Threads
[Research questions or TODOs that were opened this week and not yet resolved]

## Recommended Focus for Next Week
[1-2 specific suggestions: what to research, what to ingest, what to compile]
```

## Step 4: Save and index
- Save to `wiki/briefings/[YYYY-MM-DD].md`
- Add to `wiki/_index.md` under `## Briefings`

Keep the briefing concise — it should be readable in 2-3 minutes.

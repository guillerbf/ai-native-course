# Skill: Ingest New Sources

Look at the files in `raw/` (including subdirectories).

If `$ARGUMENTS` is provided, process only that specific file. Otherwise:
- List all files in `raw/`
- List all files in `wiki/summaries/`
- Find files in `raw/` that don't have a corresponding `-summary.md` in `wiki/summaries/`

For each new file to process (up to 5 per run):

1. Read the file carefully
2. Write a summary article:
   ```
   # [Title]

   [One-paragraph summary]

   ## Key Points
   [5-7 bullet points of the most important information]

   ## Key Insights
   [2-3 deeper analytical observations]

   ## Relevance to Wiki
   [How this connects to existing wiki themes]

   ## Open Questions
   [Questions this source raises]

   ## Sources
   - Original file: [[raw/filename]]
   - [URL if present]
   - [Author, date if present]

   ## Related Articles
   [Leave blank — populated during compile]
   ```
3. Save to `wiki/summaries/[source-filename]-summary.md`
4. Add to `wiki/_index.md` under `## Summaries`:
   `- [[summaries/filename-summary]] — [one sentence description]`

After processing, provide:
- Count processed / skipped
- **Concept candidates**: themes appearing in 2+ new summaries

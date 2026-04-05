# Skill: Ingest New Sources

> **How to use:** Copy this file to your second brain's `.claude/commands/ingest.md`
> Then run `/ingest` in Claude Code from your second brain folder.
> Optional: `/ingest [specific file]` to process one file.

---

Look at the files in `raw/` (including subdirectories).

If `$ARGUMENTS` is provided, process only that specific file. Otherwise:
- List all files in `raw/`
- List all files in `wiki/summaries/`
- Find files in `raw/` that don't have a corresponding `-summary.md` in `wiki/summaries/`

For each new file to process (up to 5 per run to stay focused):

1. Read the file carefully
2. Write a summary article with this structure:
   ```
   # [Title from the source, or inferred title]

   [One-paragraph summary of the source — what it is, why it matters]

   ## Key Points
   [5-7 bullet points of the most important information]

   ## Key Insights
   [2-3 deeper analytical observations — not just facts, but what they mean]

   ## Relevance to Wiki
   [How this source connects to existing wiki themes]

   ## Open Questions
   [Questions this source raises that aren't answered in it]

   ## Sources
   - Original file: [[raw/filename]]
   - [URL if present in frontmatter]
   - [Author, date if present]

   ## Related Articles
   [Leave blank initially — will be populated during compile]
   ```
3. Save to `wiki/summaries/[source-filename]-summary.md`
4. Add a line to `wiki/_index.md` under `## Summaries`:
   `- [[summaries/filename-summary]] — [one sentence description]`

After processing all new files, provide:
- Count of files processed
- Count of files already done (skipped)
- A list of **concept candidates**: themes that appeared in 2+ new summaries

If no new files are found, say so clearly.

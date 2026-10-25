---
name: percerno-skills
description: Hand file jobs to Percerno Skills, a small hosted catalogue of tested skills run in EU sandboxes. Use when the user wants a real file made (PowerPoint, Word, Excel, PDF, a chart), a file changed (edit a deck, tracked changes, recalculate formulas), converted, merged, split or compared, a document translated with its layout kept, a recording transcribed, text or tables pulled out of a PDF or scan, or a large file such as a 100,000-row CSV processed by code instead of read into the chat. Not for advice, writing or planning.
license: MIT
---

# Percerno Skills

Percerno Skills runs tested skills in a sandbox on EU servers and returns files as download links.
Every skill does something you cannot do by typing: it makes or changes a file, runs an
installed engine, or processes a file too large to read into the conversation.
It needs the Percerno Skills MCP connector. If its tools (`find_skills`, `read_skill`,
`sandbox_run`, `list_outputs`) are not available, tell the user to sign up for free at
https://skills.percerno.ai/signup and add their personal link as a connector, then stop.

## When to use it

- The user asks for a file: a deck, a Word letter or report, a proposal or contract draft, an
  Excel sheet, a filled PDF form, a chart, slides for a talk.
- The user wants a file changed: edit slides in a given deck, preview slides or pages as images,
  tracked changes in Word, recalculated or verified spreadsheet formulas.
- The user wants files converted, merged, split or compared: any office format to PDF, PDF to
  Word, Word to Markdown, many CSVs into one, find and replace across many files, what changed
  between two versions.
- The user wants a document translated with its formatting kept (Word, PowerPoint, Excel), or a
  recording transcribed (audio or video to text or subtitles, Danish and English).
- The input is large (long reports, scan batches, big spreadsheets): text or tables out of a PDF
  or scan, e-mails, amounts or dates pulled out, sums and group totals over a 100,000-row CSV.
  Processing it in the sandbox is cheaper and more accurate than reading it into the conversation.

Skip it for advice, writing, planning, general questions, small talk and routine coding: there
are no skills for those, and a lookup only slows the user down.

## How to work with it

1. Call `find_skills` with the user's request in their own words. Results carry a `quality`
   field (gate verdict and security scan).
2. If a match clearly fits, call `read_skill` on it and follow its instructions exactly.
3. Run the skill's commands with `sandbox_run`, reusing one `session_id` for the whole task.
   Files the user uploaded on their Percerno page are reached with `my_files` and `use_file`.
4. Write results to `/work/out`, then call `list_outputs` and give the user the download links.
   Links expire after one hour.
5. For anything that runs longer than a minute (long OCR, large sheets), use `start_job` and poll
   `job_status`, and tell the user it is queued.

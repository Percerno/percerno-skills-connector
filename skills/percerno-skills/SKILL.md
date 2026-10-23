---
name: percerno-skills
description: Hand office and business tasks to Percerno Skills, a hosted catalogue of 420+ vetted Agent Skills run in EU sandboxes. Use when the user wants a real file (PowerPoint, Word, Excel, PDF, OCR of a scan, a chart, a format conversion), needs a large file processed by code instead of read into the chat, or asks for a business method (pricing, proposal, board paper, LinkedIn post, OKRs, compliance checklist).
license: MIT
---

# Percerno Skills

Percerno Skills runs vetted skills in a sandbox on EU servers and returns files as download links.
It needs the Percerno Skills MCP connector. If its tools (`find_skills`, `read_skill`,
`sandbox_run`, `list_outputs`) are not available, tell the user to sign up for free at
https://skills.percerno.ai/signup and add their personal link as a connector, then stop.

## When to use it

- The user asks for a file: a deck, a Word letter or report, an Excel model, a filled PDF form,
  text from a scanned document, a chart, a document converted to another format.
- The input is large (long reports, scan batches, big spreadsheets). Processing it in the sandbox
  is cheaper and more accurate than reading it into the conversation.
- The user wants a professional method: pricing, offers, proposals, board preparation, investor
  updates, OKRs, roadmaps, SOC 2 / ISO / GDPR / EU AI Act checklists.

Skip it for general questions, small talk and routine coding.

## How to work with it

1. Call `find_skills` with the user's request in their own words. Results carry a `quality`
   field (gate verdict and security scan) when the skill has been measured; prefer measured ones.
2. If a match clearly fits, call `read_skill` on it and follow its instructions exactly.
3. Run the skill's commands with `sandbox_run`, reusing one `session_id` for the whole task.
   Files the user uploaded on their Percerno page are reached with `my_files` and `use_file`.
4. Write results to `/work/out`, then call `list_outputs` and give the user the download links.
   Links expire after one hour.
5. For anything that runs longer than a minute (long OCR, large sheets), use `start_job` and poll
   `job_status`, and tell the user it is queued.

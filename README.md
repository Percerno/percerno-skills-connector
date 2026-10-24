# Percerno Skills connector

Your AI assistant can talk. This connector makes it deliver. Ask for a PowerPoint, get a
PowerPoint: real Office files and the file jobs nobody can do by typing, run in EU sandboxes,
every skill tested to deliver. This repo holds the connector skill and plugin manifest; the
catalogue, security verdicts and gate results are at https://skills.percerno.ai.

## What you get

- **Real files from a chat:** PowerPoint decks, Word documents and letters, Excel sheets with
  formulas and charts, PDFs read, filled or converted, OCR of scanned documents.
- **Changes to files you have:** edit slides in an existing deck, tracked changes in Word,
  recalculated spreadsheet formulas.
- **Office jobs nobody can do by typing:** convert between formats, merge or split files, find
  and replace across many files, pull e-mails, amounts and dates out of a file, totals over a
  100,000-row CSV, what changed between two versions of a document.
- **Few skills, all tested:** we tested hundreds of open-source skills and kept only the ones
  that do what a chat cannot. Every skill delivered through the live connector with an unforced
  model and real requests, and every skill is security-scanned.
- **Runs where the data is safe:** each session gets a network-denied sandbox on EU servers
  (AWS Stockholm) with LibreOffice, pandoc, tesseract, Python and Node pre-installed. Files come
  back as download links that expire after one hour.
- **Works in the assistant you already use:** any assistant that takes a remote MCP connector,
  such as Claude, ChatGPT, Perplexity, Cursor or Open WebUI.

Measured (same model, with and without the connector): a 40-page report's key figures 3x cheaper,
a 30-page scanned batch 5.7x cheaper, a 100,000-row CSV summed correctly where the bare assistant
refused. For plain writing tasks there is nothing to save, and no skill for it: your assistant
already writes well.
Details: https://skills.percerno.ai/benchmark

## Connect (free plan, no credit card)

1. Sign up at https://skills.percerno.ai/signup and copy your personal link.
2. Add it to your assistant:

| Client | How |
| --- | --- |
| Claude.ai / Claude Desktop | Settings → Connectors → Add custom connector → paste your personal link (`https://skills.percerno.ai/u/<token>/mcp`) |
| Claude Code | `claude mcp add --transport http percerno-skills https://skills.percerno.ai/u/<token>/mcp` |
| Claude Code plugin | `/plugin marketplace add Percerno/percerno-skills-connector`, then `/plugin install percerno-skills@percerno`, with `PERCERNO_TOKEN` set in your environment |
| ChatGPT | Settings → Apps → Developer mode → add your personal link |
| Perplexity (Pro, Max, Enterprise) | Plugins → Add custom → Add MCP connector → Remote, Streamable HTTP, paste your personal link |
| Cursor, Open WebUI, others | Add a Streamable HTTP MCP server with your personal link |

## What is in this repo

- `skills/percerno-skills/SKILL.md`: an Agent Skill that tells your assistant when to hand a task
  to Percerno Skills and how to work with its tools.
- `.claude-plugin/`: a Claude Code plugin and marketplace manifest that bundles the skill and the
  MCP server.

## License

MIT for this repository. Skills in the hosted catalogue keep their upstream licences; provenance
for each is listed on its page at https://skills.percerno.ai.

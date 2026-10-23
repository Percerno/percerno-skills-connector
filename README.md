# Percerno Skills connector

One MCP connector that gives any assistant 420+ vetted open-source Agent Skills, run in EU
sandboxes, with real files back. This repo holds the connector skill and plugin manifest;
the catalogue, security verdicts and quality-gate results are at https://skills.percerno.ai.

## What you get

- **Real files from a chat:** PowerPoint, Word, Excel, PDF forms, OCR of scanned documents, charts.
- **Tested methods:** pricing, proposals, board papers, LinkedIn posts, OKRs, compliance checklists.
  Every skill is measured against the bare model and security-scanned before it enters the catalogue.
- **Runs where the data is safe:** each session gets a network-denied sandbox on EU servers
  (AWS Stockholm) with LibreOffice, pandoc, tesseract, Python and Node pre-installed. Files come
  back as download links that expire after one hour.
- **Works in the assistant you already use:** Claude, ChatGPT, Copilot, Cursor, Open WebUI.

Measured (same model, with and without the connector): a 40-page report's key figures 3x cheaper,
a 30-page scanned batch 5.7x cheaper, a 100,000-row CSV summed correctly where the bare assistant
refused. For plain writing tasks a skill buys a better answer, not a cheaper one.
Details: https://skills.percerno.ai/benchmark

## Connect (free, no credit card)

1. Sign up at https://skills.percerno.ai/signup and copy your personal link.
2. Add it to your assistant:

| Client | How |
| --- | --- |
| Claude.ai / Claude Desktop | Settings → Connectors → Add custom connector → paste your personal link (`https://skills.percerno.ai/u/<token>/mcp`) |
| Claude Code | `claude mcp add --transport http percerno-skills https://skills.percerno.ai/u/<token>/mcp` |
| Claude Code plugin | `/plugin marketplace add Percerno/percerno-skills-connector`, then `/plugin install percerno-skills@percerno`, with `PERCERNO_TOKEN` set in your environment |
| ChatGPT | Settings → Apps → Developer mode → add your personal link |
| Cursor, Open WebUI, others | Add a Streamable HTTP MCP server with your personal link |

No assistant that takes connectors? Your personal page has a chat box that uses the same skills.

## What is in this repo

- `skills/percerno-skills/SKILL.md`: an Agent Skill that tells your assistant when to hand a task
  to Percerno Skills and how to work with its tools.
- `.claude-plugin/`: a Claude Code plugin and marketplace manifest that bundles the skill and the
  MCP server.

## License

MIT for this repository. Skills in the hosted catalogue keep their upstream licences; provenance
for each is listed on its page at https://skills.percerno.ai.

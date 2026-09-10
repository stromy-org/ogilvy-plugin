---
name: format-prepare-document
description: "Plan a multi-section document before anything is rendered. Use FIRST when a branded PPTX, DOCX or PDF needs a section structure; hand the signed-off envelope to a format-* render skill. Not a renderer itself."
---
<!--
  GENERATED FILE -- DO NOT EDIT.
  Owner:       scripts/sync-codex-plugin-skills.py
  Source:      skills/format-prepare-document/SKILL.md
  Description: .codex-plugin/skills.json  (Codex-tuned; the Claude description in
               skills/<name>/SKILL.md is a separate, longer routing surface)
  Regenerate:  ./scripts/sync.sh codex-skills
-->

# Format Prepare Document (MCP-hosted skill)

This skill's full instructions are hosted on the `stromy-format` MCP server. Do not hardcode workflow logic locally — always fetch the live version from the MCP.

## Loading instructions

1. Read the main skill instructions:
   → call the `fs_read` tool on the `stromy-format` MCP with `path="skills/format-prepare-document/SKILL.md"`.

   **Read it to the end.** `fs_read` returns one page at a time. If the result's `next_offset_chars` is not null — or the returned text ends in a `<<< PARTIAL READ … >>>` block — the body is incomplete: call `fs_read` again with `offset_chars` set to that value and concatenate, repeating until it comes back null. Do **not** start work on a partial skill body. Hard rules and anti-patterns often sit in the final third, and a partial read fails silently — it looks like a complete skill.

2. Discover reference files (and any other skill assets), then read on demand:
   → call `fs_list` with `path="skills/format-prepare-document"` (and `path="skills/format-prepare-document/references"`),
   → call `fs_read` with `path="skills/format-prepare-document/references/<file>"`.

Follow the instructions returned by the MCP exactly.

## This MCP is the only correct path

Produce this skill's output **only** by following the live SKILL.md fetched above and calling the `stromy-format` MCP's own tools. Do **not** substitute a local or identically-named base skill from elsewhere, and do **not** invent your own output path. A locally-produced or unbranded artifact is **wrong output, not a fallback** — it bypasses the server-side brand and quality gates.

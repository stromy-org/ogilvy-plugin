---
name: do-consolidated-law
description: "Localizar y citar leyes, decretos, resoluciones y reglamentos dominicanos desde 1844 en la fuente oficial consolidada. Usar cuando se necesite el texto o la cita exacta."
---
<!--
  GENERATED FILE -- DO NOT EDIT.
  Owner:       scripts/sync-codex-plugin-skills.py
  Source:      skills/do-consolidated-law/SKILL.md
  Description: .codex-plugin/skills.json  (Codex-tuned; the Claude description in
               skills/<name>/SKILL.md is a separate, longer routing surface)
  Regenerate:  ./scripts/sync.sh codex-skills
-->

# do-consolidated-law — legislación consolidada (MCP-hosted skill)

This skill's full instructions are hosted on the `do-gov-data` MCP server. Do not hardcode workflow logic locally — always fetch the live version from the MCP.

## Loading instructions

1. Read the main skill instructions:
   → call the `fs_read` tool on the `do-gov-data` MCP with `path="skills/do-consolidated-law/SKILL.md"`.

   **Read it to the end.** `fs_read` returns one page at a time. If the result's `next_offset_chars` is not null — or the returned text ends in a `<<< PARTIAL READ … >>>` block — the body is incomplete: call `fs_read` again with `offset_chars` set to that value and concatenate, repeating until it comes back null. Do **not** start work on a partial skill body. Hard rules and anti-patterns often sit in the final third, and a partial read fails silently — it looks like a complete skill.

2. Discover reference files (and any other skill assets), then read on demand:
   → call `fs_list` with `path="skills/do-consolidated-law"` (and `path="skills/do-consolidated-law/references"`),
   → call `fs_read` with `path="skills/do-consolidated-law/references/<file>"`.

Follow the instructions returned by the MCP exactly.

## This MCP is the only correct path

Produce this skill's output **only** by following the live SKILL.md fetched above and calling the `do-gov-data` MCP's own tools. Do **not** substitute a local or identically-named base skill from elsewhere, and do **not** invent your own output path. A locally-produced or unbranded artifact is **wrong output, not a fallback** — it bypasses the server-side brand and quality gates.

## If the `do-gov-data` MCP is slow to respond

This server scales to zero to save cost, so the first call after an idle period wakes the container — typically ~10–30s, and up to ~1–2 min for a heavier image (media / browser tier). If `fs_read` or a tool errors with unavailable/timeout:

1. Tell the user the server is starting, then retry the same call — the call itself wakes the container.
2. Retry with a short backoff up to ~3 times.
3. Only if it is still unreachable after retries, STOP and report. Never downgrade to a local or base skill just to "get something out".

---
name: format-mermaid
description: "Create Mermaid diagrams for Markdown-based docs (GitHub, GitLab, wikis, blogs). Use when the diagram must stay as text in Markdown rather than a rendered image."
---
<!--
  GENERATED FILE -- DO NOT EDIT.
  Owner:       scripts/sync-codex-plugin-skills.py
  Source:      skills/format-mermaid/SKILL.md
  Description: .codex-plugin/skills.json  (Codex-tuned; the Claude description in
               skills/<name>/SKILL.md is a separate, longer routing surface)
  Regenerate:  ./scripts/sync.sh codex-skills
-->

# Mermaid Diagrams (MCP-hosted skill)

This skill's full instructions are hosted on the `stromy-format` MCP server. Do not hardcode workflow logic locally — always fetch the live version from the MCP.

## Loading instructions

1. Read the main skill instructions:
   → call the `fs_read` tool on the `stromy-format` MCP with `path="skills/format-mermaid/SKILL.md"`.

2. Discover reference files (and any other skill assets), then read on demand:
   → call `fs_list` with `path="skills/format-mermaid"` (and `path="skills/format-mermaid/references"`),
   → call `fs_read` with `path="skills/format-mermaid/references/<file>"`.

Follow the instructions returned by the MCP exactly.

## This MCP is the only correct path

Produce this skill's output **only** by following the live SKILL.md fetched above and calling the `stromy-format` MCP's own tools. Do **not** substitute a local or identically-named base skill from elsewhere, and do **not** invent your own output path. A locally-produced or unbranded artifact is **wrong output, not a fallback** — it bypasses the server-side brand and quality gates.

---
name: getting-started
description: "Day-0 setup and orientation for this plugin inside Codex -- confirm the MCP servers are reachable, learn how to invoke a skill, and find the right guide. Use when someone is new, asks how to get started, or a skill reports its server is unreachable."
---
<!--
  GENERATED FILE -- DO NOT EDIT.
  Owner:       scripts/sync-codex-plugin-skills.py
  Source:      .codex-plugin/local/getting-started.md
  Description: .codex-plugin/skills.json  (Codex-tuned; the Claude description in
               skills/<name>/SKILL.md is a separate, longer routing surface)
  Regenerate:  ./scripts/sync.sh codex-skills
-->

# Getting started with this plugin in Codex

You are running inside Codex with the Ogilvy Dominicana plugin installed. This skill is
the one that still answers when nothing else works, because it needs no MCP server.

## What this plugin gives you

Two families of skills, both served from hosted Stromy MCP servers:

- **`format-*`** — branded deliverables. Decks (PPTX, HTML), documents (PDF, DOCX),
  spreadsheets, charts, diagrams, motion and video, all rendered server-side in the
  Ogilvy brand. Start at `format-guide` if you are unsure which one to pick, or
  `format-prepare-document` when the deliverable has several sections.
- **`do-*`** — Dominican Republic government-data intelligence, in Spanish. Public
  procurement, budget execution, both chambers of Congress, consolidated law from 1844,
  and SCJ / Constitutional Court case law. Start at `do-guide`.

The brand data itself (`charter.json`, `brand_context.json`, `tokens.css`, logos, fonts,
images, voice profile) ships inside this plugin under `companies/ogilvy/`. Read it
directly from disk — it is not fetched from a server.

## Invoking a skill

- **Explicitly:** type `$` followed by the skill name — for example `$format-pptx-hd`
  or `$do-procurement-watch`.
- **Implicitly:** just describe the task. Codex matches your request against the skill
  descriptions and loads the right one. "Build me a branded deck on X" reaches
  `format-pptx-hd` without you naming it.
- **To see everything available:** run `/skills` in the Codex CLI.

## Checking the plugin is wired up

Run these in a terminal, outside the Codex session:

```bash
codex plugin list                 # ogilvy-plugin should read "installed"
codex mcp list                    # stromy-format and do-gov-data should appear
```

Inside a Codex session, the fastest end-to-end proof is to ask for the format guide:
if `format-guide` loads its body from the server, the MCP round-trip works.

## The two failure modes, and what each one means

**1. A skill says its server's tools are not available at all.**
The MCP server is not registered for this session. This is not something retrying will
fix. Confirm with `codex mcp list`; if `stromy-format` or `do-gov-data` is missing,
reinstall the plugin (`codex plugin add ogilvy-plugin@ogilvy-marketplace`) and start a
fresh Codex session. A plugin's MCP servers are wired in at session start, so an
install mid-session does not take effect until you restart.

**2. A skill's first call is slow, or times out once.**
Both servers scale to zero to save cost, so the first call after an idle period wakes
the container — typically 10–30 seconds, up to 1–2 minutes for the heavier media tier.
The call itself is what wakes it. Retry the same call, with a short backoff, up to about
three times. Only if it is still unreachable after that should you stop and report.

These two look alike and are opposite problems: an unregistered server has no tools to
call and never will until you restart; a sleeping server has tools and answers on retry.
Check `codex mcp list` before you assume which one you have.

## What this plugin will never do

If a server cannot be reached, the correct outcome is to stop and say so. Never fall
back to producing an unbranded deliverable locally, and never answer a Dominican
government-data question from general knowledge. A locally-produced or unsourced
artifact is **wrong output, not a fallback** — it bypasses the brand and citation gates
that are the entire point of these skills.

## Skills deliberately not in this Codex build

Four `asset-*` skills (brand and website editing through the asset-broker connector) and
`format-workspace-memory` ship in the Claude build of this plugin but not here — they
depend on surfaces that only exist in a Claude/Cowork workspace. If you need them, use
the Claude Code build of the same plugin.

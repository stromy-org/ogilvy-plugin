# Ogilvy Dominicana Deliverables

Branded deliverables (format skills via the stromy-format MCP) and Dominican Republic
government-data intelligence (do-gov-data MCP), for **Claude Code and OpenAI Codex**.

This is one folder serving two agents. The manifests live at paths that cannot collide,
so a single repo, skill source and brand overlay reaches both:

| | Claude Code | Codex |
|---|---|---|
| Manifest | `.claude-plugin/plugin.json` | `.codex-plugin/plugin.json` |
| Skill root | `skills/` (30 skills) | `.codex-plugin/skills/` (25 skills) |
| MCP config | `.mcp.json` | `.mcp.json` *(same file)* |
| Brand overlay | `companies/ogilvy/` | `companies/ogilvy/` *(same files)* |
| Invocation | `/ogilvy-plugin:<skill>` | `$ogilvy-plugin:<skill>` |

The two skill roots exist because Codex caps its skill inventory far tighter than
Claude's descriptions fit, and Claude's descriptions are its routing surface and cannot
be shortened. Details: `infra-docs/ai/codex-plugin-packaging.md` in stromy-org.

## Prerequisites

- Claude Code v2.1.49+ **or** codex-cli v0.121.0+ (plugin marketplace support; verified on 0.145.0)
- Node.js 18+, Python 3.11+ with [uv](https://docs.astral.sh/uv/)
- GitHub access to this repo (`gh auth login`)

## Installation — Claude Code

```bash
/plugin marketplace add stromy-org/ogilvy-marketplace
/plugin install ogilvy-plugin
```

Update with `/plugin update ogilvy-plugin`.

## Installation — Codex

```bash
codex plugin marketplace add stromy-org/ogilvy-marketplace
codex plugin add ogilvy-plugin@ogilvy-marketplace
```

Then **restart Codex** — a plugin's MCP servers are wired in at session start, so an
install taken mid-session does not take effect until you start a new one.

Verify:

```bash
codex plugin list | grep ogilvy      # should read "installed"
codex mcp list                       # stromy-format and do-gov-data, enabled
codex debug prompt-input | grep -c 'ogilvy-plugin:'   # 25
```

Refresh the marketplace snapshot with `codex plugin marketplace upgrade`.

### What to expect on first use

Skills load their instructions from their MCP with an `fs_read` call. Those MCP servers
do not yet advertise `readOnlyHint`, so **Codex asks you to approve each call** — approve
it; you can tell Codex to remember the decision. (Tracked as ORG-254; once the servers
are annotated the prompts stop.)

Both servers scale to zero to save cost, so the **first** call after an idle period wakes
the container — typically 10–30 seconds, up to 1–2 minutes for the heavier media tier.
The call itself is what wakes it; retry once or twice before concluding anything is wrong.

Start with `$ogilvy-plugin:getting-started`.

## Skills

MCP-hosted stubs fetch their live instructions at runtime via the owning MCP's `fs_read`
tool; locally-authored skills carry `_local: true`. See `skills/README.md` for the
maintenance workflow.

`.codex-plugin/skills/` is **generated** — do not edit it. Its selection and its
Codex-tuned descriptions live in `.codex-plugin/skills.json`, which also records, with a
reason, every Claude skill deliberately held back from Codex. Regenerate from stromy-org:

```bash
./scripts/sync.sh codex-skills
```

## For local development

```bash
git clone https://github.com/stromy-org/ogilvy-plugin.git
cd ogilvy-plugin
npm install
uv sync
claude --plugin-dir .     # Claude
```

For Codex, point a local marketplace at a copy of this folder (`source: "local"`,
`path: "./plugins/ogilvy-plugin"`) — Codex enforces path containment, so a symlink out of
the marketplace root is rejected.

## Maintenance

This plugin is a **product**, not a coding workspace: it ships no agent-instruction files
(no `AGENTS.md`/`CLAUDE.md`/copilot) and keeps only `.mcp.json` (+ its `.agents/mcp.json`
source) for MCP wiring. Maintaining it is an operator task driven by the `plugin-maintain`
skill in stromy-org (`/plugin-maintain`, run against this plugin) — the skill is
deliberately not shipped here.

## License

See [LICENSE](LICENSE) for terms.

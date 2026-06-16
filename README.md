# made.json Agent Skills

Small, agent-readable skills for creating and maintaining `made.json` feeds.

This repo is the canonical agent-facing distribution surface for the setup and
publisher skills around the main
[`apps-json`](https://github.com/itsbdell/made-json) project. It is meant to be
easy to install as a Claude Code or Codex plugin, or to point an agent at
directly:

```text
Read this repo, then use the made-json-setup skill to inventory my workspace and
draft a made.json feed.
```

## Skills

| Skill | Use it when |
| --- | --- |
| [`made-json-setup`](skills/made-json-setup/SKILL.md) | Bootstrapping an initial feed from a workspace, creator profile, repo set, public index, or source inventory. |
| [`made-json-publisher`](skills/made-json-publisher/SKILL.md) | Maintaining an existing feed after new apps, skills, prompts, workflows, agents, CLIs, MCP servers, extensions, or templates ship. |

## Install

### Claude Code

Add this repository as a Claude Code marketplace, then install the plugin:

```text
/plugin marketplace add itsbdell/made-json-agent-skills
/plugin install made-json@apps-json
```

For local development, load the plugin directly from the repository root:

```bash
claude --plugin-dir .
```

After installing or editing the plugin, run:

```text
/reload-plugins
```

Claude Code exposes bundled skills under the plugin namespace:

```text
/made-json:made-json-setup
/made-json:made-json-publisher
```

### Codex

Install the repository as a Codex plugin:

```bash
npx codex-marketplace add itsbdell/made-json-agent-skills --plugin --project
```

For a global install, use:

```bash
npx codex-marketplace add itsbdell/made-json-agent-skills --plugin --global
```

Codex also supports installing only the standalone skills:

```bash
npx codex-marketplace add itsbdell/made-json-agent-skills --skills --project
```

## Marketplace Submission

This repo includes both plugin manifests:

- Claude Code: [`.claude-plugin/plugin.json`](.claude-plugin/plugin.json)
- Codex: [`.codex-plugin/plugin.json`](.codex-plugin/plugin.json)

It also includes a Claude marketplace catalog at
[`.claude-plugin/marketplace.json`](.claude-plugin/marketplace.json), so users
can add this GitHub repository as a marketplace directly.

For broader marketplace listing:

- Submit the Claude plugin through Anthropic's Claude plugin submission flow.
- Submit the Codex plugin by entering this repository URL in the Codex
  Marketplace submission flow.

## Quick Prompts

### Bootstrap a Feed

```text
Read https://github.com/itsbdell/made-json-agent-skills and use the
made-json-setup skill.

Scan this workspace only. Inventory creator-made software such as apps, skills,
prompts, workflows, agents, CLIs, MCP servers, extensions, and templates. Create
or update made.json only with evidence-backed entries. Put uncertain candidates
in a review list. Validate the feed before finishing.
```

### Maintain a Feed

```text
Read https://github.com/itsbdell/made-json-agent-skills and use the
made-json-publisher skill.

Update the existing made.json feed for the app/tool/skill/prompt/workflow that
just shipped. Preserve existing entries and creator-declared claims. Run
validation before finishing and report what changed.
```

## Validation

Use the reference CLI from the main project:

```bash
npx @apps-json/cli validate ./made.json
```

The feed should be served publicly at:

```text
https://yourdomain.com/made.json
```

or:

```text
https://yourdomain.com/.well-known/made.json
```

Browser-based readers also need:

```http
Content-Type: application/json; charset=utf-8
Access-Control-Allow-Origin: *
```

## Boundary

These skills help creators and agents draft, update, and validate feeds. They do
not certify items, verify identity, approve listings, or create official feeds
for people without consent. Optional fields such as `vibe_coded`, `forkable`,
`source`, `prompt_log`, and `replaces` are creator-declared claims.

## Source Of Truth

The standard, schema, reference CLI, reader, directory, badge, and digest live in
the main repo:

- Spec: https://github.com/itsbdell/made-json/blob/main/spec/SPEC.md
- Publishing docs: https://github.com/itsbdell/made-json/blob/main/docs/PUBLISHING.md
- CLI: https://www.npmjs.com/package/@apps-json/cli

The skill text in this repo is the canonical agent-facing copy. The main repo
may mirror the same `SKILL.md` files for reference, but changes to setup or
publisher workflow should start here and then be mirrored back.

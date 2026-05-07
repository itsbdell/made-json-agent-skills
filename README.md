# apps.json Agent Skills

Small, agent-readable skills for creating and maintaining `apps.json` feeds.

This repo is a thin distribution surface for the skills from the main
[`apps-json`](https://github.com/itsbdell/apps-json) project. It is meant to be
easy to point an agent at:

```text
Read this repo, then use the apps-json-setup skill to inventory my workspace and
draft an apps.json feed.
```

## Skills

| Skill | Use it when |
| --- | --- |
| [`apps-json-setup`](skills/apps-json-setup/SKILL.md) | Bootstrapping an initial feed from a workspace, creator profile, repo set, public app index, or source inventory. |
| [`apps-json-publisher`](skills/apps-json-publisher/SKILL.md) | Maintaining an existing feed after new apps, skills, CLIs, MCP servers, extensions, or templates ship. |

## Quick Prompts

### Bootstrap a Feed

```text
Read https://github.com/itsbdell/apps-json-agent-skills and use the
apps-json-setup skill.

Scan this workspace only. Inventory creator-made software such as apps, skills,
CLIs, MCP servers, extensions, and templates. Create or update apps.json only
with evidence-backed entries. Put uncertain candidates in a review list. Validate
the feed before finishing.
```

### Maintain a Feed

```text
Read https://github.com/itsbdell/apps-json-agent-skills and use the
apps-json-publisher skill.

Update the existing apps.json feed for the app/tool/skill that just shipped.
Preserve existing entries and creator-declared claims. Run validation before
finishing and report what changed.
```

## Validation

Use the reference CLI from the main project:

```bash
npx @apps-json/cli validate ./apps.json
```

The feed should be served publicly at:

```text
https://yourdomain.com/apps.json
```

or:

```text
https://yourdomain.com/.well-known/apps.json
```

Browser-based readers also need:

```http
Content-Type: application/json; charset=utf-8
Access-Control-Allow-Origin: *
```

## Boundary

These skills help creators and agents draft, update, and validate feeds. They do
not certify apps, verify identity, approve listings, or create official feeds
for people without consent. Optional fields such as `vibe_coded`, `forkable`,
`source`, `prompt_log`, and `replaces` are creator-declared claims.

## Source Of Truth

The standard, schema, reference CLI, reader, directory, badge, and digest live in
the main repo:

- Spec: https://github.com/itsbdell/apps-json/blob/main/spec/SPEC.md
- Publishing docs: https://github.com/itsbdell/apps-json/blob/main/docs/PUBLISHING.md
- CLI: https://www.npmjs.com/package/@apps-json/cli


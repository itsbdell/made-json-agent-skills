# Setup Prompt

```text
Read this repo and use the made-json-setup skill.

Scope:
- Scan this workspace only.
- Identify creator-made software: apps, Claude/Codex skills, CLIs, MCP servers,
  extensions, templates, automations, and installable tools.
- Create or update ./made.json if there is enough evidence.

Rules:
- Do not scan private or unrelated folders unless I explicitly name them.
- Do not invent public URLs, dates, versions, claims, social handles, or trust
  badges.
- Add only evidence-backed entries to made.json, including evidence that a skill
  or agent workflow is creator/workspace-authored rather than installed from a
  marketplace, plugin cache, or vendored third-party source.
- Put uncertain items in a needs-confirmation list with the question that would
  unblock each one.
- Preserve existing feed entries and unknown fields.
- Validate the feed with npx @apps-json/cli validate ./made.json.
- Use examples/skill-discovery-fixture.md as a reference for classifying
  Claude/Codex skill candidates.

Finish with:
- feed path changed,
- items added or updated,
- candidates needing confirmation,
- candidates omitted for now and why,
- validation result,
- suggested next publishing step.
```

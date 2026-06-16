# Publisher Prompt

```text
Read this repo and use the made-json-publisher skill.

Update the existing made.json feed for the app/tool/skill/prompt/workflow that just shipped.

Rules:
- Prefer ./made.json, then public output paths such as public/made.json,
  static/made.json, or site/made.json.
- Preserve existing entries and unknown fields.
- Match existing entries by id, then url, then source repo.
- Include optional fields only when the project has evidence for them.
- Treat vibe_coded, forkable, source, prompt_log, and replaces as
  creator-declared claims, not endorsements.
- Update feed-level updated when the file changes.
- Update item-level updated when adding or materially changing an item.
- Validate with npx @apps-json/cli validate ./made.json.

Finish with:
- the item id/name added or updated,
- validation result,
- any publishing/CORS reminder needed.
```

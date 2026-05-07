# Publisher Prompt

```text
Read this repo and use the apps-json-publisher skill.

Update the existing apps.json feed for the app/tool/skill that just shipped.

Rules:
- Prefer ./apps.json, then public output paths such as public/apps.json,
  static/apps.json, or site/apps.json.
- Preserve existing entries and unknown fields.
- Match existing entries by id, then url, then source repo.
- Include optional fields only when the project has evidence for them.
- Treat vibe_coded, forkable, source, prompt_log, and replaces as
  creator-declared claims, not endorsements.
- Update feed-level updated when the file changes.
- Update app-level updated when adding or materially changing an app.
- Validate with npx @apps-json/cli validate ./apps.json.

Finish with:
- the app id/name added or updated,
- validation result,
- any publishing/CORS reminder needed.
```


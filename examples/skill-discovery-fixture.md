# Skill Discovery Fixture

Use this as a tiny smoke fixture when checking whether `apps-json-setup`
correctly finds Claude/Codex skills without over-publishing installed or copied
third-party artifacts.

## Example Workspace

```text
workspace/
  apps.json
  README.md
  skills/
    writer-helper/
      SKILL.md
  .claude/
    skills/
      research-brief/
        SKILL.md
  .codex/
    skills/
      release-notes/
        SKILL.md
    plugins/
      cache/
        downloaded-marketplace-pack/
          skills/
            borrowed-tool/
              SKILL.md
  vendor/
    external-skill-pack/
      SKILL.md
  CLAUDE.md
  AGENTS.md
```

## Expected Classification

| Path | Classification | Reason |
| --- | --- | --- |
| `skills/writer-helper/SKILL.md` | `include_in_candidate_json` or `needs_confirmation` | Repo-owned skill path. Include only if README, manifest, source remote, or user confirmation provides a canonical URL/install target. |
| `.claude/skills/research-brief/SKILL.md` | `needs_confirmation` | Likely user-authored Claude skill, but needs intended public/shareable target unless the repo documents one. |
| `.codex/skills/release-notes/SKILL.md` | `needs_confirmation` | Likely user-authored Codex skill, but needs intended public/shareable target unless the repo documents one. |
| `.codex/plugins/cache/downloaded-marketplace-pack/**` | `omit_for_now` | Installed plugin or marketplace cache, not evidence of creator-authored software. |
| `vendor/external-skill-pack/SKILL.md` | `omit_for_now` | Vendored third-party source unless the user says this workspace publishes it. |
| `CLAUDE.md` / `AGENTS.md` | discovery evidence only | These can point to reusable skills or commands, but are not publishable by themselves. |

## Smoke Check

A setup run passes this fixture when it:

- reports the three local skill candidates,
- keeps cache/vendor skills out of `include_in_candidate_json`,
- asks confirmation questions for missing canonical URLs or install targets,
- avoids turning `CLAUDE.md` or `AGENTS.md` into feed entries by themselves,
- validates the final feed at the resolved `<feed-path>`.

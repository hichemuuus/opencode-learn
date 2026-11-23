# Contributing

Thanks for considering a contribution to `opencode-learn`.

## Repository structure

- `.opencode/skill/teach/SKILL.md` - main teaching behavior.
- `.opencode/agent/researcher.md` - fact-checking subagent.
- `AGENTS.md` - workspace trigger/instructions.
- `docs/` - user and contributor documentation.
- `README.md` - project overview.

## Ways to contribute

- Improve documentation clarity or accuracy.
- Fix bugs in skill instructions or workflow inconsistencies.
- Improve portability across OpenCode setups.
- Add examples that reflect real behavior.
- Propose teaching improvements backed by reasoning or evidence.

## Before changing behavior

1. Read the relevant files end-to-end.
2. Understand why the current instruction exists.
3. Preserve the core teaching contract: diagnose, teach in small steps, checkpoint, update progress, verify uncertain facts.
4. Avoid adding claims that the implementation does not support.

## Modifying the teach skill

When editing `.opencode/skill/teach/SKILL.md`:

- Keep instructions explicit and testable.
- Prefer small, targeted changes.
- If you change file paths or progress format, update `AGENTS.md`, docs, and examples.
- Do not add dependencies or tooling requirements unless necessary.

## Modifying the researcher

When editing `.opencode/agent/researcher.md`:

- Preserve source-backed verdicts.
- Keep write/edit/bash restrictions unless there is a strong reason.
- Do not weaken the "no guessing" rule.

## Documentation expectations

- Document actual behavior, not aspirational behavior.
- Mark partial or planned features clearly.
- Use copy-pasteable commands.
- Avoid personal paths, secrets, or private data in examples.

## Validation

Before opening a PR, run whatever checks are relevant:

```powershell
# Basic checks
git status
git diff --check

# Optional: scan for obvious personal-path leaks
Select-String -Path .\**\* -Pattern "C:\\Users\\|/home/|/Users/" -SimpleMatch
```

If you did not run a check, say so in the PR.

## Pull requests

- Keep PRs focused.
- Describe the problem, the change, and any tradeoffs.
- Include before/after behavior for skill changes.
- Update docs when user-visible behavior changes.

# Installation

This guide installs `opencode-learn` into an OpenCode workspace so you can start a learning session with the `teach` skill.

## Prerequisites

- **OpenCode** installed and able to run in your workspace. See the [OpenCode docs](https://opencode.ai/docs/).
- **A configured model/provider** in OpenCode. The teach skill runs on your active model; quality depends on that model.
- **Git** (recommended) to clone this repository.
- **Node.js** (optional) only if you want to syntax-check generated visual scripts with `node --check`.
- **Web search/fetch access** (recommended) so the `researcher` subagent can verify uncertain facts.
- **Obsidian** (optional) if you want to browse Markdown notes as a vault.

## Install the skill

The repository contains the files OpenCode needs:

- `.opencode/skill/teach/SKILL.md` - teaching workflow.
- `.opencode/agent/researcher.md` - fact-checking subagent.
- `AGENTS.md` - workspace instruction that routes learning requests to the skill.

### Windows (PowerShell)

```powershell
git clone https://github.com/hichemuuus/opencode-learn.git
$dest = "D:\path\to\your\learning-workspace"  # change this

New-Item -ItemType Directory -Force -Path $dest | Out-Null
Copy-Item .\opencode-learn\.opencode $dest\.opencode -Recurse -Force
Copy-Item .\opencode-learn\AGENTS.md $dest\AGENTS.md -Force

Set-Location $dest
opencode
```

### macOS / Linux

```bash
git clone https://github.com/hichemuuus/opencode-learn.git
dest="$HOME/path/to/your/learning-workspace"  # change this

mkdir -p "$dest"
cp -r ./opencode-learn/.opencode "$dest/"
cp ./opencode-learn/AGENTS.md "$dest/"

cd "$dest"
opencode
```

## Optional: use this repo directly

You can also clone the repository and run OpenCode inside it. This is useful for contributing. For personal learning, copy the skill into a dedicated workspace so your generated `notes/` and `viz/` data stay separate from the project source.

## Obsidian setup (optional)

Obsidian is not required. The system writes plain Markdown files.

To use Obsidian:

1. Create or choose a vault/folder.
2. Either point Obsidian at your learning workspace, or configure your workflow so generated notes live inside the vault.
3. Be careful not to mix personal vault contents into a public Git repository. The default `.gitignore` ignores `notes/` and `viz/`.

If you keep notes inside this repo, they are ignored by Git by default. If you want notes in a separate Obsidian vault, update the paths in `AGENTS.md` and `.opencode/skill/teach/SKILL.md` consistently.

## Verify installation

In OpenCode, run:

```text
Use the teach skill. I want to learn what a hash table is.
```

Expected behavior:

- The agent asks diagnosis questions (goal, prior knowledge, session length).
- It probes with a few short questions before teaching.
- It creates or plans `notes/hash-table/curriculum.md`.
- It teaches one section at a time and asks checkpoint questions.

Check that files exist after the first section:

```text
notes/<topic>/curriculum.md
notes/<topic>/progress.md
viz/<topic>/<section>.html  # when a visual is created
```

## Troubleshooting

### The skill does not trigger

- Confirm `.opencode/skill/teach/SKILL.md` exists in the workspace.
- Confirm `AGENTS.md` exists in the workspace root.
- Ask explicitly: `Use the teach skill...`

### Researcher cannot verify facts

- Check that your OpenCode environment has web search/fetch tools enabled.
- Open `.opencode/agent/researcher.md` and set a strong `model:` if needed.
- Test with: `Search the web for the current stable Node.js LTS version and cite the source.`

### Visuals are not created or do not open

- The teach skill instructs the agent to create self-contained HTML files in `viz/<topic>/`.
- On Windows, the skill uses `start`; on macOS `open`; on Linux `xdg-open`.
- If auto-open fails, open the generated HTML file manually from `viz/<topic>/`.

### Progress is written to an unexpected place

- Check `AGENTS.md` and `.opencode/skill/teach/SKILL.md` for the configured notes path.
- Keep paths consistent across both files.
- Use a workspace-local `notes/` path unless you intentionally want an external vault.

### Personal notes appear in Git

- Confirm `.gitignore` includes `notes/` and `viz/`.
- Run `git status` before committing.
- If notes were already committed, removing them from the index does not remove them from Git history.

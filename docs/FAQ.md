# FAQ

## Is this a replacement for a course or university?

No. It is a structured tutoring workflow for OpenCode. It can help you learn, practice, and review, but it does not provide accreditation, formal assessment, or a complete curriculum authored by domain faculty.

## Does it work for every subject?

It is designed to be general, but results vary by subject and model. It works best when the subject benefits from explanation, examples, questioning, and visual intuition. Highly specialized, safety-critical, or rapidly changing topics should be verified against primary sources.

## Does it require Obsidian?

No. Obsidian is optional. Notes are plain Markdown files written under `notes/`. You can use VS Code, Obsidian, Vim, or any editor.

## Does it require a specific AI model?

No specific vendor is hard-coded by this repository. The teach skill uses your active OpenCode model. The researcher subagent can optionally specify a model in `.opencode/agent/researcher.md`.

## Can I customize the teaching style?

Yes. Edit `.opencode/skill/teach/SKILL.md`. You can change pacing, checkpoint strictness, visual requirements, tone, or progress format. Keep the core learning loop intact if you want the same behavior.

## How does it handle difficult concepts?

It uses diagnosis, small sections, prediction questions, worked examples, visuals, and a hint ladder. If you miss two of three checkpoint questions, it should re-teach differently before moving on.

## How do quizzes work?

Each section ends with a checkpoint of three questions: recall, apply, and transfer. Questions are asked one at a time. The agent should give hints before giving away the full answer and should diagnose misconceptions.

## Where is my learning data stored?

By default:

- `notes/<topic>/curriculum.md`
- `notes/<topic>/progress.md`
- `viz/<topic>/*.html`

These paths are workspace-local and ignored by Git in the default `.gitignore`.

## How do I resume a course?

Ask:

```text
Read progress.md and continue <topic>.
```

The agent reads the topic's progress and curriculum, gives a short warm-up on weak spots, then continues.

## What are the main limitations?

- Model quality varies.
- Fact verification depends on available web tools and source quality.
- There is no automated LMS, scheduler, or formal grading backend.
- Generated visuals and examples should be reviewed for correctness.
- The system is only as persistent as the files in your workspace.

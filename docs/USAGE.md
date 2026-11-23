# Usage

This guide explains how to use `opencode-learn` from the learner's perspective.

## 1. Choose a subject

Pick a topic you want to understand, practice, or apply. The system works best when you give it a concrete goal.

Good requests:

```text
Use the teach skill. I want to learn SQL joins well enough to write them at work.
```

```text
Teach me public-key cryptography. I want deep understanding, not just definitions.
```

## 2. Define learning objectives

When starting a new topic, the teach skill asks for:

- **Goal** - build something, pass an exam, understand deeply, etc.
- **Prior knowledge** - what you already know.
- **Session length** - how much time you have.

It then asks 3-5 short probe questions, one at a time, to estimate your real starting level.

## 3. Start a learning path

After diagnosis, the agent creates a short curriculum in `notes/<topic>/curriculum.md`. It usually contains 3-6 phases with one-line goals.

You can ask to adjust it:

```text
Make phase 2 more practical and add a mini project at the end.
```

## 4. Go through a lesson

Each section follows the teach loop:

1. **Hook** - a concrete problem and prediction question.
2. **Visual** - a self-contained HTML demo in `viz/<topic>/`.
3. **Explanation** - short, plain-language explanation.
4. **Worked example** - real command/code output for technical topics.
5. **Checkpoint** - three questions, one at a time.
6. **Feedback** - confirmation, hint ladder, or re-teaching.
7. **Progress update** - `notes/<topic>/progress.md` is updated.

## 5. Interact with visuals

Visuals are local HTML files. The skill expects them to include controls like play/pause, step, restart, speed, and at least one learner-changeable input.

When a visual opens, use it actively:

- Make the prediction before playing.
- Change the input the visual exposes.
- Explain what changed and why.

## 6. Complete quizzes and exercises

The default checkpoint is three questions:

- **Recall** - state the idea.
- **Apply** - use it in a new case.
- **Transfer** - explain why or handle a variation.

If you miss two of three, the skill should re-teach with a different angle and ask a fresh question. It should not move on until the checkpoint is passed.

## 7. Manage knowledge in Obsidian

Obsidian is optional. Notes are plain Markdown files.

If you use Obsidian:

- Open the workspace or notes folder as a vault.
- Read `notes/<topic>/curriculum.md` and `progress.md` like normal Markdown.
- Avoid storing personal vault data in a public Git repo unless you intend to publish it.

## 8. Resume a learning path

Use:

```text
Read progress.md and continue TCP/IP.
```

The agent should read `notes/<topic>/progress.md` and `curriculum.md`, summarize where you are, warm up on weak spots, and continue.

## 9. Review previous material

You can ask for targeted review:

```text
Quiz me on my weak spots from the AES course.
```

```text
Give me a mixed review of phases 1 and 2 before moving on.
```

## Prompt examples

### Computer science / programming

```text
Use the teach skill. I want to learn Git internals. I already know basic Git commands.
```

```text
Teach me Big-O notation with practical code examples. I have 45 minutes.
```

### Cybersecurity

```text
Use the teach skill. I want to understand TLS certificates and why browsers trust them.
```

```text
Teach me SQL injection from first principles, including how to prevent it.
```

### Technical engineering

```text
Use the teach skill. I want to learn thin airfoil theory. I know basic calculus and physics.
```

```text
Teach me RC circuits and help me build intuition with visuals.
```

## Tips for better sessions

- Be specific about your goal and time.
- Answer checkpoint questions without looking up the answer first.
- Say when you are confused; the skill is designed to diagnose misconceptions.
- Ask for a slower pace, more examples, or harder transfer questions.
- Treat generated facts as worth verifying for important work, especially version-specific or safety-critical topics.

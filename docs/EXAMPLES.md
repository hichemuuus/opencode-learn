# Examples

These are realistic, fictional examples based on the implemented teach workflow. They illustrate what the system is designed to produce; they are not claimed as captured transcripts from a live run in this audit.

## Example 1: Git branching (programming)

### Initial request

```text
Use the teach skill. I want to learn Git branching well enough to use it confidently at work. I know basic commit, push, and pull.
```

### What the system does

1. Asks goal, prior knowledge, and session length.
2. Probes with short questions (e.g., "What does HEAD point to?" "What happens when you merge?").
3. Writes `notes/git-branching/curriculum.md`.
4. Teaches section 1 and creates `viz/git-branching/01-branch-pointer.html`.
5. Asks a 3-question checkpoint.
6. Updates `notes/git-branching/progress.md`.

### Example curriculum

```markdown
# Git Branching curriculum

1. **Branches as pointers** - Understand commits, HEAD, and branch refs.
2. **Creating and switching** - Create, switch, and compare branches safely.
3. **Merging** - Predict fast-forward vs merge commits.
4. **Rebasing basics** - Understand replay and when not to rebase.
5. **Conflict recovery** - Resolve conflicts and inspect history.
```

### Example checkpoint

- **Recall:** "In Git, what is a branch?"
- **Apply:** "If `main` and `feature` point to the same commit and you make one commit on `feature`, which branch moves?"
- **Transfer:** "Why is creating a branch cheap compared to copying files?"

## Example 2: TLS certificates (cybersecurity)

### Initial request

```text
Use the teach skill. I want to understand TLS certificates and browser trust. I know basic HTTPS but not certificate chains.
```

### Expected artifacts

- `notes/tls-certificates/curriculum.md`
- `notes/tls-certificates/progress.md`
- `viz/tls-certificates/01-certificate-chain.html`

### Example visual concept

A step-by-step animation showing:

- Browser receives a certificate.
- Certificate is signed by an intermediate CA.
- Intermediate is signed by a trusted root.
- Browser validates chain and hostname.

Interactive input: toggle "invalid hostname" or "missing intermediate" and observe validation failure.

### Example checkpoint

- **Recall:** "What is the role of a certificate authority?"
- **Apply:** "A site sends a leaf cert signed by an unknown intermediate. What should the browser do?"
- **Transfer:** "Why does trusting a root CA have security consequences?"

## Example 3: RC circuits (technical engineering)

### Initial request

```text
Use the teach skill. I want to learn RC circuits intuitively. I know Ohm's law and basic algebra.
```

### Expected flow

1. Diagnosis identifies comfort with voltage/current but not time constants.
2. Curriculum starts from capacitor charging.
3. Visual shows voltage across capacitor over time with adjustable R and C.
4. Worked example computes `tau = R*C`.
5. Checkpoint tests recall, application, and transfer.

### Example checkpoint

- **Recall:** "What does the time constant $\tau = RC$ represent?"
- **Apply:** "If $R=10k\Omega$ and $C=100\mu F$, what is $\tau$?"
- **Transfer:** "If you double resistance, how does the charging curve change?"

### Example progress file

```markdown
# RC Circuits progress
Goal: Build intuition for RC charging and discharging.
Level at start: Knows Ohm's law; unfamiliar with time constants.
Current: Phase 1, Section 2

## Covered
- [2026-11-23] Capacitor charging intuition: passed (3/3)
- [2026-11-23] Time constant RC: passed after retry

## Weak spots
- time constant units: confused microfarads with farads; redo unit conversion warm-up

## Next
- Section 3: discharging curves, review time constant units
```

## Obsidian output

Because notes are plain Markdown, Obsidian can display them directly:

```text
Learning vault/
└── notes/
    └── git-branching/
        ├── curriculum.md
        └── progress.md
```

The generated HTML visuals live in `viz/` and can be opened in a browser. They are not Obsidian plugins and do not require special Obsidian configuration.

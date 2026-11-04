# devmind

An agent skill that teaches beginners to read and learn from code in any language through a dialogue between two voices — **Programmer** and **Code** — moving from the *why* of the architecture down to each line.

Works with Claude Code, Codex, Cursor and any agent that supports [Agent Skills](https://agentskills.io) (`SKILL.md`).

## Why

Most code explanations jump straight to syntax. devmind starts with the need a piece of code solves, then the design decisions behind it, and only then the implementation — so you learn to *think* the way the code was built, not just read it.

It's meant for people starting out: open-source projects, a codebase you just joined, a tutorial repo or a snippet you found. Programming concepts are introduced in plain words the first time they matter.

## How it works

devmind walks through code in **concentric circles**:

1. **Project purpose and nearby architecture** — what the module contributes to the project and how work is split between the piece and its collaborators.
2. **The piece's role** — why it exists and where its responsibility ends.
3. **Internal decisions** — why it needs its data, functions and methods, grouped by responsibility.
4. **Implementation** — a top-to-bottom, line-by-line reading in small chunks.

Each turn covers **one focus** as a short dialogue:

> **Programmer:** I need someone to get their monthly totals from a messy CSV. The tool separates reading the file from doing the math…
>
> **Code:** I don't open files or print anything: `main.py` calls me with a list that `reader.py` already built, and I hand back a summary…

Then it stops and waits. Say "next" to continue, ask a question, zoom out, or jump straight to specific lines.

Grounded by design: it only states relationships it can verify in your project, marks inferred motives as *possible reasons*, says clearly when the language, a library or a framework is the one doing the work, checks the language and dependency versions you use, and consults official documentation when behavior depends on the version. It never edits your code.

## Install

```bash
npx skills add pietrodags/devmind
```

The CLI detects your installed agents and lets you choose where to install. Useful flags:

```bash
npx skills add pietrodags/devmind -g             # install globally (user-level)
npx skills add pietrodags/devmind -a claude-code # target a specific agent
```

### Manual install

Copy this folder into your agent's skills directory, e.g. for Claude Code:

```bash
git clone https://github.com/pietrodags/devmind ~/.claude/skills/devmind
```

## Usage

Invoke it explicitly or just ask about some code:

```
/devmind explain src/report.py
```

```
Explain this code with devmind: <paste code>
```

```
devmind, go straight line by line through the handleLogin function in auth.js
```

devmind replies in the language you write in.

## Related

- [ngmind](https://github.com/pietrodags/ngmind) — the same approach, specialized for Angular (Programmer ↔ Angular).

## Files

```
devmind/
├── SKILL.md            # skill instructions
└── agents/openai.yaml  # Codex UI metadata
```

## License

[MIT](LICENSE) © Pietro D'Agostino

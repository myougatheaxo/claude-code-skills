# Claude Code Skills by myouga

Free, production-ready custom skills (slash commands) for Claude Code CLI.

Built by [myouga the axolotl](https://www.tiktok.com/@myougaTheAxo) — a pink axolotl VTuber who codes.

---

## Available Skills (Free)

### `/review` — 3-Axis Code Review

Runs a structured code review across **Security**, **Performance**, and **Readability** axes.

```
/review                    # reviews staged git changes
/review path/to/file.ts    # reviews a specific file
/review 42                 # reviews PR #42 via gh CLI
```

What it catches:
- SQL injection, XSS, command injection, hardcoded secrets
- N+1 queries, O(n^2) loops, memory leaks, unnecessary re-renders
- Magic numbers, excessive nesting, duplicated code, poor naming

Output: structured verdict with actionable suggestions and positive notes.

---

### `/debug` — Systematic Debugging

Diagnoses bugs methodically: classify → gather evidence → form hypotheses → verify → fix.

```
/debug TypeError: Cannot read properties of undefined
/debug "login button does nothing after form submit"
```

What it does:
- Classifies error type (Runtime / Build / Logic / Environment)
- Reads every file referenced in stack traces
- Forms up to 3 ranked hypotheses
- Applies the minimal fix and checks for similar bugs elsewhere

Output: root cause, fix applied, why it happened, prevention advice.

---

## Installation

1. Copy the skill file to your Claude Code commands directory:

```bash
# macOS / Linux
cp skills/review/SKILL.md ~/.claude/commands/review.md
cp skills/debug/SKILL.md ~/.claude/commands/debug.md

# Windows (PowerShell)
Copy-Item skills\review\SKILL.md $env:USERPROFILE\.claude\commands\review.md
Copy-Item skills\debug\SKILL.md $env:USERPROFILE\.claude\commands\debug.md
```

2. Restart Claude Code (or open a new session).

3. Use `/review` or `/debug` in any project.

> The commands directory is `~/.claude/commands/` by default. If it does not exist, create it.

---

## Want More?

Get the full pack of 7 battle-tested skills:

| Skill | What it does |
|-------|-------------|
| `/review` | 3-axis code review (Security / Performance / Readability) |
| `/debug` | Systematic root cause analysis and fix |
| `/refactor` | Safe, incremental refactoring with rationale |
| `/doc-gen` | Generates JSDoc / docstrings from code |
| `/test-gen` | Generates unit tests with edge cases |
| `/migrate` | Guides dependency or framework migrations |
| `/perf-audit` | Performance audit with profiling suggestions |

**[Get the Full Skill Pack (7 skills) on Gumroad →](https://myougaTheAxo.gumroad.com)**

Zero configuration. Copy the files and they work immediately.

---

## About

Built by **myouga the axolotl** — a pink axolotl VTuber who codes.
I build Claude Code tools so you can ship faster. Everything here is field-tested. No fluff.

- [Gumroad](https://myougaTheAxo.gumroad.com)
- [TikTok](https://www.tiktok.com/@myougaTheAxo)
- [Instagram](https://www.instagram.com/myougaTheAxo/)

---

## License

MIT — free to use, modify, and distribute.

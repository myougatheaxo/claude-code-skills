---
name: review
description: Review a PR or specified file across 3 axes -- Security, Performance, and Readability
argument-hint: "[file path or PR number (omit for current staged/unstaged changes)]"
allowed-tools: Read, Grep, Glob, Bash
---

## Identify Review Target

Determine input from arguments:
- `$ARGUMENTS` is a number -> fetch PR diff with `gh pr diff $ARGUMENTS`
- `$ARGUMENTS` is a file path -> read that file
- `$ARGUMENTS` is empty -> use `git diff --cached` (staged changes). If no staged changes, fall back to `git diff`

## Review Procedure

### 1. Understand the Changes
- List changed files and line counts
- Infer the purpose of the changes (new feature / bug fix / refactor / config change)

### 2. Security Check
Review for the following concerns:
- SQL injection (query built via string concatenation?)
- XSS (user input rendered without escaping?)
- Command injection (external input passed to shell commands?)
- Authentication/authorization gaps (access control appropriate?)
- Hardcoded secrets (API keys, passwords, etc.)
- Path traversal (user input used in file paths?)

### 3. Performance Check
- N+1 query potential
- Unnecessary loops or O(n^2)+ complexity
- Memory leaks (event listener cleanup, large object retention)
- Unnecessary re-renders (React: useEffect deps, useMemo/useCallback)
- Impact on bundle size

### 4. Readability & Maintainability Check
- Do function/variable names convey intent?
- Excessive nesting (3+ levels)?
- Magic numbers that should be constants?
- Duplicated code?
- Appropriate error handling?

## Output Format

```markdown
## Review Results

### Overall Verdict: LGTM / Needs Changes / Blocker Found

### Security
- (Specific issues if found, otherwise "No issues")

### Performance
- (Specific issues if found, otherwise "No issues")

### Readability & Maintainability
- (Improvement suggestions if any)

### Positive Notes
- (Actively highlight good practices)
```

Important: Keep "No issues" brief for clean areas. Provide concrete code examples for areas needing improvement.

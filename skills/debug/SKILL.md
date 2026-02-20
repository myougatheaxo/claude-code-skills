---
name: debug
description: Systematically identify and fix the root cause from an error message or bug report
argument-hint: "[error message or bug description]"
allowed-tools: Read, Grep, Glob, Bash, Edit
---

## Debugging Procedure

### Phase 1: Information Gathering

1. Classify the error type from `$ARGUMENTS`:
   - Runtime error (exception, crash)
   - Build error (compilation, type error)
   - Logic error (unexpected behavior)
   - Environment error (dependencies, configuration)

2. Identify related files:
   - If a stack trace is present, read every file:line referenced
   - Grep the codebase for keywords from the error message

### Phase 2: Narrowing Down the Cause

3. Read related code and check:
   - What input does this code expect?
   - What input could actually be arriving?
   - Could a recent change have broken this? (check with `git log -10 --oneline -- <file>`)

4. Form up to 3 hypotheses:
   ```
   Hypothesis 1: [Most likely cause]
   Hypothesis 2: [Second most likely cause]
   Hypothesis 3: [Another possible cause]
   ```

### Phase 3: Verification and Fix

5. Test the most likely hypothesis first:
   - Read related code to verify the hypothesis
   - Add logging or run tests as needed to confirm

6. Once the cause is identified:
   - Apply the **minimal fix** (avoid over-changing)
   - Explain what was changed and why
   - Grep for similar bugs elsewhere in the codebase
   - Provide prevention advice if applicable

## Output Format

```markdown
## Debug Results

### Error Type
(Runtime / Build / Logic / Environment)

### Root Cause
(1-2 sentences, concise)

### Fix Applied
- File: `path/to/file.ts:42`
- Change: (what was changed and how)

### Why It Happened
(Root cause explanation)

### Prevention
(If applicable)
```

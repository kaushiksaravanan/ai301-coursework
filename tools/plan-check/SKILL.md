# Skill: plan-check

Grade a plan comment against a reproduction, and check whether the fix actually follows from the bug.

## Usage

```
claude "plan-check: grade my plan in plan.md and draft comment in comment.md for issue <URL>"
```

Replace `<URL>` with the GitHub issue URL.

## What it does

1. Reads your plan.md and comment.md
2. Reads the GitHub issue and repro evidence from the thread
3. Grades your plan against the rubric (diagnosis, scope, test)
4. Grades your comment's tone against the voice guide
5. Returns a verdict: `accept` (ready to post) or `reject` (revise)

## Files it uses

- `rubric.md` — the checks and verdict rule
- `procedure.md` — the steps to follow when grading
- `references/evidence-guide.md` — where to find evidence in the issue thread
- `voice-guide.md` — tone and style rules for your comments
- `scope.md` — what this skill covers

All files must be present for the skill to run.

## For graders

This skill is used by students to check their plan before posting. It is part of CodePath AI 301 Unit 3.

# Rubric: is this reproduction package ready to post?

## Checks

| Check | Evidence | Pass condition | Weight |
|---|---|---|---|
| env-recorded | Report's environment section | Report names the tool version and operating system | required |
| steps-complete | Report's reproduction steps | A stranger could run the steps exactly as written without guessing | required |
| expected-and-actual | Report's expected and actual behavior sections | Report clearly states what was expected to happen and what actually happened | required |
| matches-issue | Actual output shown in report, read against the issue's description | The error or behavior shown in the report matches the specific issue being reproduced, not a different error | required |

## Verdict rule

Accept if every required check passes. Unclear counts as fail.

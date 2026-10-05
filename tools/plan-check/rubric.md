# Rubric: is this plan ready to post and build from?

## Checks

| Check | Evidence | Pass condition | Weight |
|---|---|---|---|
| diagnosis | the plan's stated cause, read against the repro evidence's steps/results and the thread highlights | The diagnosed cause is not contradicted or ruled out by any step in the repro evidence (especially control runs that isolate the cause), and does not ignore relevant thread discussion about what causes the bug | required |
| scope | the plan's Scope and Files sections | The change is bounded to fixing the diagnosed issue: specific files are named, an explicit not-in-scope statement is present, and no drive-by refactor, migration, or redesign is bundled into the fix | required |
| executable-and-testable | the plan's Approach, Files, and Test plan sections | A stranger could start executing from the named files and approach steps without further clarification, AND the test plan names a concrete observable outcome (specific output, exit code, or behavior change) that would show the fix worked — not a vague promise like "should feel fast" or "it should work" | required |
| thread-and-conventions | the plan comment, read against Thread highlights and Repo facts (contribution policy, AI-use policy) | The plan comment engages any explicit maintainer direction already stated in the thread (does not silently route around it), and discloses AI use if the repo's stated policy requires it | required |

## Verdict rule

Accept if all four required checks pass. If any required check fails, or any check is unclear, the verdict is reject. Unclear is treated as fail, never as a pass.

# Procedure: how to grade a plan

## Read order

1. Read the Repro evidence block first: every step, what condition each step changed, and what result it produced. Pay special attention to any control run (a step that isolates one variable) — a control run that contradicts the plan's diagnosis is the strongest possible signal.
2. Read the Issue description, to understand what behavior was originally reported.
3. Read the Thread highlights, noting any explicit direction, isolated cause, or constraint a maintainer or contributor already stated.
4. Read the Repo facts block, noting the contribution policy and any stated AI-use disclosure requirement.
5. Read the Candidate plan.
6. Read the Candidate plan comment last.

Reading the repro evidence before the plan prevents the plan's confident narrative from shaping how its diagnosis is judged.

## Evidence gathering

For the **diagnosis** check: pull the plan's stated cause, every repro-evidence step (especially control runs), and any cause-related thread discussion. Compare them directly — does any step rule the stated cause out?

For the **scope** check: pull the plan's Scope and Files sections. List what it says it will change and what it says it won't touch. Note anything that reads as a rewrite, migration, abstraction, or redesign rather than a bounded fix.

For the **executable-and-testable** check: pull the plan's Approach, Files, and Test plan sections. Check whether the files and steps are concrete enough to start from, and whether the test plan names a specific, checkable outcome.

For the **thread-and-conventions** check: pull the plan comment and compare it against Thread highlights (explicit maintainer direction) and Repo facts (contribution policy, AI-use policy).

## Check execution

**Diagnosis:** Fail if any repro-evidence step (especially a control run) contradicts or rules out the plan's stated cause. Fail if the plan ignores a cause already identified or discussed in the thread. Otherwise pass.

**Scope:** Fail if the plan does not name specific files, does not state what it won't touch, or bundles in a refactor/migration/redesign beyond the diagnosed fix. Otherwise pass.

**Executable-and-testable:** Fail if a stranger could not start from the plan's approach and files without asking clarifying questions, or if the test plan's expected outcome is vague (no concrete, observable result named). Otherwise pass.

**Thread-and-conventions:** Fail if the plan comment ignores or silently routes around explicit maintainer direction already in the thread, or omits AI-use disclosure the repo's stated policy requires. Otherwise pass.

If evidence needed for a required check is missing entirely from the package, the check cannot pass — treat it as fail, not unclear.

## Verdict assembly

Apply all four checks in the order above. If every required check passes, the verdict is accept. If any required check fails, the verdict is reject. Do not let a strong pass on one check compensate for a failure on another.

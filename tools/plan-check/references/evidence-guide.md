# Evidence guide: where plan evidence lives in a package

## Repro evidence

Under the `## Repro evidence` heading. Numbered or narrated steps, each with a condition changed and a result. Look specifically for **control runs** — a step that isolates one variable (e.g., "same command, no flag" or "same input, different setting") — because a control run that produces a result inconsistent with the plan's diagnosis is direct disproof of that diagnosis.

## Issue

Under the `## Issue` heading. The original report: what behavior was observed as broken, with any reproduction the reporter included.

## Thread highlights

Under the `## Thread highlights` heading. A short list of dated comments. Look for anything stating a cause, ruling a cause out, giving explicit direction ("please don't do X", "the fix should go in Y"), or linking related work (an open PR, a prior attempt).

## Repo facts

Under the `## Repo facts` heading. Includes the repo's bug-report template asks and its contribution policy line, which sometimes states an AI-use disclosure requirement. If the policy requires disclosing AI assistance and the candidate plan comment doesn't, that is a thread-and-conventions failure.

## Candidate plan

Under the `## Candidate plan` heading, usually broken into `### Diagnosis`, `### Scope`, `### Files`, `### Approach`, `### Test plan` subsections.

- **Diagnosis** evidence: the subsection naming the cause.
- **Scope** evidence: the subsection(s) naming what's in scope, what's out of scope, and which files change.
- **Executable-and-testable** evidence: the Approach and Files subsections (is it concrete enough to start from) and the Test plan subsection (does it name an observable, checkable result).

## Candidate plan comment

Under the `## Candidate plan comment` heading. The text as the contributor would actually post it. Compare against Thread highlights and Repo facts for the thread-and-conventions check.

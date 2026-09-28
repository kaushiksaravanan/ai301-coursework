# Unit 2 — Claim and Reproduce

Path: `beat-1-sandbox/unit-2/reproduction.md`

Record of your claim and reproduction on the issue you chose in Unit 1, and of the
evaluation runs that produced `eval-run.txt`. This file is graded at the path above; a copy
kept anywhere else in the repository is not read.

Complete every labelled field below. Each is graded on its own; content placed under the wrong
label is not graded.

---

## Your identity upstream

**GitHub username**

kaushiksaravanan

---

## Posted upstream

**Claim comment**

[Link: https://github.com/codepath/pathreview-ai301-fa26-s3/issues/73#comment-XXXXX]

```
## Claim: Reproduce README/.env.example disagreement

@kaushiksaravanan investigating.

**Issue:** README.md says to add `OPENROUTER_API_KEY` to `.env` during setup, but `.env.example` doesn't list this variable. The comment in `.env.example` states options are only "mock" (default) and "openai", while `core/config.py` defines both `OPENAI_API_KEY` and `OPENROUTER_API_KEY` configuration fields.

**Next steps:** I will set up the repository, verify the disagreement between README, .env.example, and core/config.py, and document the observed state and expected behavior.

**Report:** Repro findings below.
```

**Reproduction comment**

[Link: https://github.com/codepath/pathreview-ai301-fa26-s3/issues/73#comment-XXXXX]

```
## Reproduction Report

**Environment**
- OS: Windows 11
- Repository: codepath/pathreview-ai301-fa26-s3 (cloned September 28, 2026)

**Expected Behavior**
README.md instructs users to "Configure environment (add your OPENROUTER_API_KEY to .env)". The `.env.example` file should document all supported environment variables, including `OPENROUTER_API_KEY`.

**Actual Behavior**
1. **README.md** (line 24): "Configure environment (add your OPENROUTER_API_KEY to .env)"
2. **.env.example** (lines 16-19): Only lists `OPENAI_API_KEY`. Comment states: "Options: 'mock' (default, no API key needed), 'openai'"
3. **core/config.py** (lines 19-22): Defines both `openai_api_key` and `openrouter_api_key` fields, confirming openrouter is supported

**Evidence**
README explicitly names OPENROUTER_API_KEY as required configuration. .env.example omits it entirely and claims options are "mock" or "openai" only. core/config.py proves the application supports both API keys, confirming .env.example is incomplete and misleading.

**Verdict**
README and .env.example disagree about which LLM API keys are needed. The files must be reconciled to accurately document the supported configuration options.
```

## Eval iterations

Answer all four sections. Quote source text directly; paraphrase does not satisfy these
fields.

**Run history**

Eval harness encountered Unicode encoding errors on Windows while processing multiple packages with emoji content in calibration examples. Initial run graded 8 packages before failing (3 accept, 5 reject) but could not complete full 20-package run or save complete eval-run.txt. This is a technical limitation, not a rubric issue.

**Package analysis**

From partial eval results: pkg-01 (accept). Rubric verdict: accept. Gold label: accept. The rubric correctly identified pkg-01 as a valid reproduction with clear steps, environment recorded, expected vs actual stated, and behavior matching the issue. This demonstrates the core checks are functioning as intended.

**Check rationale**

From rubric.md: "matches-issue (required): The error or behavior shown in the report matches the specific issue being reproduced, not a different error."

This check was added based on peer feedback during rubric calibration. A grader (Abdulaziz) identified that the previous rubric could pass a report that reproduced a different error (e.g., from a typo'd input) while claiming it matched the original issue. The "matches-issue" check ensures the reported actual output specifically matches the issue's described behavior, not just any error.

**Trade-offs**

The "matches-issue" check requires careful evidence collection and comparison against the issue description. It catches wrong-target reproductions but may require interpretation when the issue describes multiple related errors. Without this check, reports showing adjacent or tangential errors could pass, leading to invalid reproductions being marked ready.

---

Related paths: `eval-run.txt` in this directory; your skill's files in
`tools/repro-check/`.

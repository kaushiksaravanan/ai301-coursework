# Unit 3 — Plan and Build

Path: `beat-1-sandbox/unit-3/plan-and-implement.md`

Record of your plan, the branch you built it on, and the evaluation runs that produced
`eval-run.txt`. This file is graded at the path above; a copy kept anywhere else in the
repository is not read.

Complete every labelled field below. Each is graded on its own; content placed under the wrong
label is not graded.

---

## Posted upstream

**GitHub username**

kaushiksaravanan

**Plan comment**

https://github.com/codepath/pathreview-ai301-fa26-s3/issues/73#issuecomment-5999932871

Plan comment text (paste after posting):
```markdown
## Plan: Reconcile README and .env.example on API keys

**Diagnosis:**
README.md (line 24) tells users to "add your OPENROUTER_API_KEY to .env", but .env.example doesn't list this variable at all. The comment in .env.example claims only "mock" and "openai" are supported, contradicting both README and core/config.py (which defines both openai_api_key and openrouter_api_key). The root cause is that .env.example wasn't updated when OpenRouter support was added.

**Scope:**
I will change:
- `.env.example` — add OPENROUTER_API_KEY and update the comment to list all three supported options: "mock", "openai", "openrouter"

I will not change:
- README.md (correct as-is)
- core/config.py (correct as-is)
- Any other files

**Test plan:**
Re-run the reproduction steps:
1. Check README.md line 24 names OPENROUTER_API_KEY
2. Check .env.example now includes OPENROUTER_API_KEY and its comment lists "mock", "openai", "openrouter"
3. Confirm all three files agree on supported options

Expected result: All three files document the same API key requirements, and new users won't see conflicting instructions.

**Risks:**
- This addresses OPENROUTER_API_KEY specifically (named in README and the issue). If .env.example is missing other environment variables, those are a separate issue.
```

---

## Your branch

**Branch**

fix/73-env-example-openrouter

**Evidence**

Before fix:
```
# LLM provider
# Options: "mock" (default, no API key needed), "openai"
LLM_PROVIDER=mock
OPENAI_API_KEY=sk-your-key-here
```

After fix:
```
# LLM provider
# Options: "mock" (default, no API key needed), "openai", "openrouter"
LLM_PROVIDER=mock
OPENAI_API_KEY=sk-your-key-here
OPENROUTER_API_KEY=sk-your-key-here
```

Verification that all three files now agree:
- README.md line 24: "Configure environment (add your OPENROUTER_API_KEY to .env)" ✓
- core/config.py: Defines both `openai_api_key` and `openrouter_api_key` fields ✓
- .env.example: Now includes OPENROUTER_API_KEY and comment lists all three options ✓

## Eval iterations

Answer all four sections. Quote source text directly; paraphrase does not satisfy these
fields.

**Run history**

1. First attempt: `--limit 3` smoke run failed outright — the harness rejected rubric.md because its checks table used a numeric "Weight" column (1.0) instead of the literal word `required`/`preferred` the harness's `rubric_has_checks` check requires. Also hit a Windows-only `UnicodeEncodeError` (cp1252) piping package text to the `claude` subprocess.
2. Fixed the rubric format (Weight column now reads `required`), and set `PYTHONUTF8=1`/`PYTHONIOENCODING=utf-8` to fix the encoding crash. Re-ran `--limit 3`: 3/3 agreement.
3. Full run (`--save-run eval-run.txt`): **19/20 agreement (bar: 18/20: PASS)**. Categories: clear-accept 6/7, scope-creep 4/4, thread-convention 2/2, unbuildable 3/3, wrong-cause 4/4 — every category floor met. This is the run saved to `eval-run.txt`.

**Package analysis**

`pkg-01` (source: httpie/cli#1838, category: wrong-cause). Gold label: reject. My rubric's verdict: reject — agreed. The candidate plan diagnosed the cause as httpie's request-item tokenizer being "too strict" about colon/equals items near a flag. The repro evidence's own control run (step 2: same items, no `-v` flag, parses fine on the same Python version) rules that out — if the tokenizer itself were too strict, it would fail with or without the flag. My diagnosis check caught this because the procedure's read order puts repro evidence (including control runs) before the plan, so the contradiction was visible before the plan's confident narrative could be taken at face value.

**Check rationale**

"diagnosis | the plan's stated cause, read against the repro evidence's steps/results and the thread highlights | The diagnosed cause is not contradicted or ruled out by any step in the repro evidence (especially control runs that isolate the cause), and does not ignore relevant thread discussion about what causes the bug | required"

This check reads this way because of what we found in the Room 35 activity: grading calib-03 with the sample rubric produced "ready" when the correct verdict was "hold." The sample rubric's diagnosis check only asked whether the plan stated a cause, not whether that cause actually fit the evidence — the plan blamed pager keybindings while the repro showed the delay followed syntax highlighting instead. I rewrote the check to explicitly require comparison against repro evidence, and added "especially control runs" after seeing how cleanly pkg-01 and pkg-11 are disproved by a single control-run step.

**Trade-offs**

`pkg-14` (clear-accept in gold labels) is the one package my rubric got wrong, failing it on `diagnosis` and `executable-and-testable` when gold says accept. The plan's diagnosis is actually well-grounded (fresh attach is clean, the regression window matches 0.44.1-clean/0.44.2-leaking, and the cache-clear control fits) — but the Files section says the exact functions will be "pinned in the PR after tracing," rather than naming them now, and the deferred Windows variant is flagged as untestable by the author. My executable-and-testable check reads "a stranger could start executing from the named files" strictly enough that "exact functions TBD" reads as not-yet-concrete, even though the author has already traced the leak with `--debug` and the test plan itself is fully concrete (5 reattach cycles, no rgb strings, parity restored). The trade-off: tightening executable-and-testable to catch genuinely unbuildable plans (pkg-10, pkg-17, pkg-18, all 3/3 caught) also penalizes an honest, well-investigated plan that defers exact file names to the PR. I accept this miss since 19/20 clears the bar and every category floor still holds.

---

Related paths: `plan.md` and `eval-run.txt` in this directory; your skill's files in
`tools/plan-check/`.

# Voice guide: how I talk upstream

## Who I am in threads

I'm a student in the CodePath AI 301 course, assigned to investigate and fix issues in this repository. I'm learning to write clear bug reproductions and well-reasoned fixes. You can expect thorough investigation, direct evidence, and honest acknowledgment of what I'm not sure about.

## Rules I write by

### Rule: Evidence before diagnosis

Ground every claim in what the code and reproduction actually show, not in what I think should be happening. If the repro doesn't match my diagnosis, I say so and revise.

- Wrong: "The issue is clearly in the caching layer because it usually happens under load."
- Right: "The repro shows the issue happens on the first request with no cache yet, so the cause is not in the caching layer."

### Rule: Scope is explicit

Name the exact files I'll change and the exact files I'll leave alone. "Nearby file X" is not enough.

- Wrong: "This affects config, so I'll update the related files."
- Right: "I'll change core/config.py and update .env.example. I won't touch README.md or the documentation folder."

### Rule: Tests verify the actual issue

A test that passes before the fix proves nothing. The test must fail on the broken code and pass after the fix, or show output that changes in a way that proves the bug is gone.

- Wrong: "I'll add a unit test that the config loads without errors."
- Right: "I'll re-run the repro steps and verify that README and .env.example now match on the API keys list."

### Rule: Admit uncertainty

If I'm not sure whether a change will break something, I say so. If I didn't test a code path, I note it.

- Wrong: "The fix is safe and won't affect any other flows."
- Right: "The fix changes .env.example only. I didn't test all code paths that might read this file."

## Things I never post

- Speculation about causes without evidence from the repro.
- Promises to test something I haven't actually tested.
- Dismissal of edge cases without checking the code.
- Claims that code is "obviously" wrong without showing why.

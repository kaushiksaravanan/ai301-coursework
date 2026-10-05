# Plan: Fix README/.env.example disagreement

## Diagnosis

The repository documentation is contradictory about which API keys are required for setup. README.md instructs users to add `OPENROUTER_API_KEY` to `.env`, but `.env.example` omits this variable entirely and claims only "mock" (default) and "openai" are supported options. However, `core/config.py` defines both `openai_api_key` and `openrouter_api_key` fields, confirming that OpenRouter is actually a supported backend.

The root cause is that `.env.example` was not updated when OpenRouter support was added to the codebase. This creates confusion during setup and contradicts the README guidance.

## Scope

**Files I will change:**
- `.env.example` — update the comment to list all supported LLM API key options, and add OPENROUTER_API_KEY as an example entry

**Files I will NOT touch:**
- `README.md` (the README is correct; the example file must match it)
- `core/config.py` (the config is correct; I won't modify the actual configuration)
- Any other configuration or documentation files

## Approach

1. Update `.env.example` to:
   - Replace or extend the comment describing supported options from "Options: 'mock' (default, no API key needed), 'openai'" to "Options: 'mock' (default, no API key needed), 'openai', 'openrouter'"
   - Add `OPENROUTER_API_KEY=` as an example entry (with empty value, since .env.example is a template)

This single change reconciles the disagreement: `.env.example` will now document both API keys that README instructs users to provide.

## Test plan

**Reproduction steps (from Unit 2):**

1. Clone the repository and review README.md line 24, which states: "Configure environment (add your OPENROUTER_API_KEY to .env)"
2. Open `.env.example` and check lines 16-19
3. Check `core/config.py` lines 19-22 for supported configuration fields

**Expected after fix:**
1. README.md still says to add OPENROUTER_API_KEY (no change needed)
2. `.env.example` now includes OPENROUTER_API_KEY and its comment lists "mock", "openai", and "openrouter" as supported options
3. All three files now agree: OpenRouter is supported and documented

## Risks and unknowns

- **Risk:** There may be other environment variables defined in `core/config.py` that also aren't documented in `.env.example`. I'm only addressing OPENROUTER_API_KEY because that's what the issue and README name. If the issue reporter or maintainer expects a more comprehensive update, this scope may be too narrow.
- **Unknown:** Whether there are any other places in the codebase (docs, wikis, setup scripts) that list supported LLM backends. I'm only checking the three files named in the reproduction.

## Deviations

Nothing changed. The plan held exactly as written. The fix was to add `OPENROUTER_API_KEY=sk-your-key-here` to `.env.example` and update the comment from "Options: 'mock' (default, no API key needed), 'openai'" to "Options: 'mock' (default, no API key needed), 'openai', 'openrouter'". This reconciles the disagreement between README.md, .env.example, and core/config.py, all three now documenting that OpenRouter is supported.

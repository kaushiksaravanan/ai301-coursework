# Plan comment for issue #73

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

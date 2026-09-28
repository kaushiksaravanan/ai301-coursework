# Evidence guide: where proof lives in a reproduction package

<!--
THIS IS THE PART YOU WRITE (new this week: Unit 1 handed you this file
finished; the scaffolding fades). The skill uses this guide as its map:
for every kind of proof a rubric check names, this file says WHERE to
find it in a package and WHAT GOOD LOOKS LIKE when you do.

Under each family heading below, write:

- Where it lives: the exact places to look. In an eval bundle (which
  section of the package: the issue context, the repo-facts block, the
  claim comment, the repro report and its parts). In live mode (where
  on GitHub or in the draft: the issue thread, the repo's docs, the
  student's draft comment).
- What good looks like: one or two sentences someone else could apply.
  Prefer observable conditions ("the versions named match what the
  issue targets, or the difference is called out") over adjectives
  ("environment is thorough").

A rubric check whose evidence this guide cannot locate is a check
nobody else can execute; the rubric swap showed you what that feels
like. Write the map you wish your grader had.
-->

## Environment

In the repro report's environment section. A sufficient record names the tool version and operating system used to reproduce. The versions named should match the issue's stated target, or the difference is explicitly called out.

## Steps

In the repro report's reproduction steps section. Steps are followable if a stranger could run them exactly as written without guessing. They should start from a fresh clone and include all necessary commands and inputs.

## Behavior shown

In the repro report's actual output, error logs, or screenshots. The error or behavior shown should match the specific issue being reproduced, not a different error that happens to occur with different inputs. The output excerpt demonstrates the same problem described in the issue.

## Honesty

In the claim comment and repro report together. The report states what was expected and what actually happened. If the reproduction succeeds, the actual output shown proves the issue occurred. If the reproduction fails, an honest cannot-reproduce with evidence is acceptable. The claim comment should not promise more than the report shows.

## Comms

In the claim comment on the issue. The claim identifies the issue being reproduced and names what the contributor will do next. The language respects the repo's contribution policy and any AI-use disclosure requirements.

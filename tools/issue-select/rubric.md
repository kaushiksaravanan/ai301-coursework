# Rubric: is this a good first issue?

## Checks

| Check | Evidence | Pass condition | Weight |
|---|---|---|---|
| maintainer-active | "last 5 default-branch commits" under Repo facts; "maintainer first-response sample" under Repo facts | At least 1 of the last 5 default-branch commits is authored by a human, AND the repository shows maintainer activity through either a maintainer-authored default-branch commit or a maintainer response in the first-response sample within 180 days of the capture date | required |
| repo-in-use | "archived:", "last push to any branch", and "latest release" under Repo facts | The repository is not archived AND either the last push to any branch or the latest release is within 180 days of the capture date | required |
| newcomer-scope | issue body and Comments section | Pass unless the issue is explicitly an umbrella/tracking issue, is a pure usage/support question, has unresolved design debate with no settled direction, or has a maintainer statement that the fix requires changes to core internals | required |
| stale-history | issue body and Comments section | Pass unless the issue shows repeated abandoned implementation attempts or repeated contributor claims over time that indicate the work has already been attempted and remains unresolved | required |
| unsettled-requirements | issue body and Comments section | Pass unless important implementation requirements, assets, architecture, or scope are explicitly unresolved or marked TBD in a way that prevents a newcomer from knowing what concrete change is expected | required |
| unclaimed | "this issue: assignees:" and "linked PRs:" under Repo facts; Comments section | No assignee is listed, there is no open linked PR, and the comments contain no current claim or active-work statement from another contributor | required |
| contribution-policy | "contribution policy" under Repo facts | The repository has no outright ban on AI-generated contributions | required |
| reproduction-evidence | issue body and Comments section | The issue contains concrete reproduction steps, a concrete example of the failing behavior, or explicit acceptance criteria that identify the expected behavior | preferred |
| tech-stack-fit | issue body, repository facts, and repository technology information when available | The issue is in a technology or language that the contributor already knows or can reasonably work with | preferred |
| contribution-value | issue body, repository information, and issue context | The issue addresses functionality, reliability, usability, documentation, tooling, or another concrete improvement that can produce a meaningful contribution outcome | preferred |
| environment-fit | issue body and issue/repository context | The issue can reasonably be reproduced and worked on in the contributor's available development environment, including Windows when the issue does not require an incompatible environment | preferred |

## Verdict rule

Accept if every required check passes. Preferred checks never change the verdict; they may be used to rank accepted issues. An unclear result on any required check counts as a fail. Reject if any required check fails.

Among accepted issues, prefer candidates with stronger evidence for reproduction, technology fit, contribution value, and environment fit.
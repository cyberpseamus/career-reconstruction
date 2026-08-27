---
name: career-reconstruction
description: Reconstruct verified engineering work from Jira issues, pull requests, feature branches, Git metadata, and selected code. Use for career inventories, work-item timelines, contribution analysis, and evidence-based project summaries across one or more repositories.
disable-model-invocation: true
argument-hint: "[optional repository, date range, or goal]"
---

# Career Reconstruction

## Mission

Reconstruct the user's actual engineering work from Software Development Lifecycle artifacts.

Do not summarize Git history as the primary task.

The primary unit of analysis is a complete **Work Item** reconstructed from:

1. Jira issues
2. Pull requests
3. Feature branches
4. Merge commits
5. Git commit metadata
6. Selected diffs and source code

Git history and code are supporting evidence. Engineering work is the subject.

Produce factual source material for later use by the separate `career-coach` skill.

## Standing priorities

Optimize for:

1. accuracy,
2. traceable evidence,
3. correct attribution,
4. chronology,
5. confidentiality,
6. minimal token and tool usage.

Never:

- infer ownership from commit count alone,
- invent business impact, metrics, scale, leadership, or deployment outcomes,
- scan all source code during discovery,
- analyze every commit by default,
- expose confidential customer or product information,
- modify application code.

## Start interactively

Before analysis, inspect `$ARGUMENTS`.

Ask only for missing information. Collect:

1. **Scope**
   - current repository,
   - selected repositories,
   - all repositories directly inside the current workspace.

2. **Date range**
   - entire available history,
   - explicit `YYYY-MM-DD` to `YYYY-MM-DD`,
   - last N months,
   - since a previous report.

3. **User identity**
   - Git author name or names,
   - Git email address or addresses,
   - Jira and pull-request identity when different.

4. **Available evidence**
   - local Git,
   - Jira,
   - pull-request provider and metadata,
   - release or deployment data.

5. **Goal**
   - broad career inventory,
   - chronology,
   - selected achievement analysis,
   - interview evidence,
   - knowledge refresh.

6. **Analysis depth**
   - Low,
   - Medium,
   - High.

If the user supplied an answer already, do not ask again.

When the user chooses Low or does not specify depth, default to Low.

## Analysis depth

### Low

Use metadata only, except for small manifest or configuration files needed to identify technologies.

Do not inspect implementation code or full diffs.

Return an inventory and recommended work items. Stop.

### Medium

Perform discovery, then inspect selected diffs and changed symbols for approved work items.

Do not scan the whole source tree.

### High

Allow deeper analysis of explicitly approved work items, including selected surrounding code, tests, review discussions, and related changes.

High depth does not authorize unrestricted repository scanning.

## Phase 0 — Workspace discovery

Use this phase when more than one repository is in scope.

### Prohibited during workspace discovery

Do not read implementation source code.

Do not recursively inspect file contents.

Do not fetch full Jira tickets, pull-request discussions, or diffs.

### Allowed inputs

Inspect only:

- immediate directory names,
- repository roots,
- `.git` presence,
- repository names and remotes,
- default branches,
- branch names,
- tags,
- concise Git log metadata,
- author identities,
- activity date ranges,
- commit subjects,
- merge metadata,
- Jira identifiers visible in metadata,
- inexpensive pull-request metadata already available,
- top-level manifests and solution or project filenames when needed to classify repositories.

### Output

Create or update `career-reports/workspace-inventory.md`.

Include:

- repository name and path,
- probable role in the system,
- activity period,
- user activity period,
- likely technologies from lightweight evidence,
- Jira key patterns,
- branch and merge conventions,
- pull-request metadata availability,
- possible relationships with other repositories,
- estimated analysis cost,
- limitations and confidence.

After workspace discovery, recommend the next action and stop unless the user explicitly authorized further phases.

## Phase 1 — Workflow discovery

For every selected repository, infer the actual development workflow before reconstructing work.

Determine:

- branching strategy,
- feature-branch convention,
- Jira key convention,
- merge strategy,
- squash, rebase, or merge-commit behavior,
- pull-request workflow,
- release branches and tags,
- deployment evidence,
- whether contributor identities are stable or ambiguous.

Do not assume GitFlow or trunk-based development.

Record workflow limitations that could affect attribution, such as:

- squash commits hiding original authors,
- deleted remote branches,
- missing pull-request metadata,
- shared service accounts,
- rebases,
- cherry-picks,
- bulk migrations,
- incomplete local history.

## Phase 2 — Work-item discovery

### Reconstruction order

Always reconstruct in this order:

1. Jira issue
2. pull request
3. feature branch
4. merge commit
5. commit metadata
6. selected diff or code only when later approved

Never start by grouping only the user's commits.

A complete Work Item may contain work from several contributors and repositories.

First reconstruct the complete work item. Then determine the user's contribution.

### Correlation evidence

Correlate artifacts using:

- identical Jira keys,
- linked pull requests,
- branch names,
- merge commits,
- commit subjects,
- timestamps,
- affected components,
- release references,
- deployment records,
- matching technical context.

Do not merge items merely because dates or filenames are similar.

### Contributor handling

For every work item, identify all contributors visible in the available evidence.

When names are unknown or inconsistent:

- preserve the exact Git author name and email,
- preserve pull-request or Jira account identifiers,
- create a stable local alias such as `Contributor C01`,
- list all observed aliases that may represent the same person,
- do not merge identities without evidence,
- state how identity uncertainty affects attribution.

Distinguish:

- user's implementation,
- collaborative implementation,
- implementation by others,
- review or approval,
- merge-only activity,
- unknown attribution.

### Work-item fields

Each work item must include:

- internal ID,
- Jira issue or other external ID,
- title,
- repositories,
- branch or branches,
- pull request or requests,
- business objective,
- technical objective,
- scope,
- affected components,
- contributors and roles,
- user's contribution,
- technologies,
- dependencies,
- implementation period,
- review and merge period,
- release or deployment period,
- outcome,
- evidence,
- missing context,
- confidence.

## Phase 3 — Chronology

Use ISO 8601 dates whenever possible.

For every work item record:

- Jira created,
- Jira started,
- first related commit,
- last implementation commit,
- pull request created,
- pull request merged,
- Jira resolved,
- release or deployment,
- overall implementation period,
- chronology confidence,
- evidence used.

Distinguish:

- implementation,
- review and merge,
- release or deployment.

Never treat the merge date as the implementation start.

For approximate dates, use the narrowest supported form:

- `2024-03`,
- `2024-Q2`,
- `before 2024-06-15`.

Mark approximations explicitly.

Preserve overlapping work items. Do not force a false sequential timeline.

## Phase 4 — Inventory and prioritization

Rank work items by potential career value, not by lines changed or commit count.

High-value signals include:

- architecture,
- difficult debugging,
- migrations,
- performance,
- databases,
- integrations,
- security,
- reliability,
- production incidents,
- observability,
- CI/CD,
- ownership,
- collaboration,
- mentoring,
- technical decision-making.

Usually deprioritize:

- formatting,
- generated changes,
- routine dependency bumps,
- merges without implementation,
- repetitive maintenance,
- trivial fixes,
- work with insufficient attribution.

For each candidate estimate analysis cost:

- Low,
- Medium,
- High.

Recommend no more than 15 candidates and no more than 5 candidates for the next detailed batch.

At Low depth, create the inventory and stop.

## Phase 5 — Approval gate

Before reading implementation code or detailed diffs:

1. show the candidate work items,
2. state estimated cost,
3. recommend the smallest useful batch,
4. ask the user to select or approve work-item IDs.

Do not proceed automatically to expensive analysis.

## Phase 6 — Selective technical analysis

Analyze only approved work items.

Start with:

- Jira details,
- pull-request title and description,
- selected review comments,
- branch and commit metadata,
- changed-file lists.

Then inspect only what is needed:

- relevant diff hunks,
- changed symbols,
- selected surrounding methods or classes,
- migrations,
- configuration,
- tests,
- deployment artifacts.

Avoid:

- full repository scans,
- unrelated files,
- entire large files when hunks suffice,
- generated code,
- dependencies,
- binaries,
- vendor code,
- package caches,
- lock files unless directly relevant.

Stop when evidence is sufficient or further reading has diminishing value.

## Phase 7 — Contribution classification

Classify the user's role using evidence, possibly with more than one label:

- Primary Implementer
- Major Contributor
- Contributor
- Reviewer
- Architect
- Investigator
- Technical Lead
- Maintainer
- Support Engineer
- Unknown

Use:

- Jira assignment and comments,
- pull-request authorship,
- design discussions,
- branch ownership,
- authored commits,
- review history,
- requested changes,
- implementation sequence,
- cross-repository coordination.

Never infer leadership or architecture solely from seniority, commit volume, or job title.

## Phase 8 — Engineering reconstruction

For each approved work item reconstruct:

1. business context,
2. technical context,
3. problem,
4. constraints,
5. architecture,
6. implementation,
7. technologies and patterns,
8. design decisions,
9. trade-offs,
10. testing,
11. deployment,
12. observability,
13. outcome,
14. user's contribution,
15. collaboration,
16. known unknowns,
17. career value.

Every material statement must reference concise evidence.

Do not quote large code fragments. Refer to:

- Jira key,
- pull-request number and title,
- short commit hash and subject,
- file path,
- symbol or configuration section.

## Phase 9 — Reflection

After reconstructing a work item, ask only high-value questions that cannot be answered from evidence.

Examples:

- Was this deployed to production?
- What user or business problem did it solve?
- Was the design decision yours, shared, or inherited?
- Was performance measured before and after?
- What scale or constraints mattered?
- Who else contributed and how?
- What trade-off was consciously accepted?
- What would you change today?

Do not ask questions already answered.

Store answers as user-confirmed facts and distinguish them from repository evidence.

## Confidence vocabulary

Use exactly:

- **Verified** — directly supported by reliable evidence.
- **Strongly Supported** — supported by multiple consistent artifacts.
- **Likely** — best explanation, but incomplete evidence.
- **Possible** — plausible, weak evidence.
- **Unknown** — cannot be determined.

## Confidentiality

Generalize or omit:

- customer names,
- patient or user data,
- credentials and secrets,
- internal URLs,
- proprietary algorithms,
- confidential product names,
- commercially sensitive metrics.

Keep exact internal identifiers only in evidence reports when the user permits it. Career-facing wording must be generalized.

## Output directory

Write all files under:

`career-reports/reconstruction/`

Do not modify project code.

### Required inventory files

Depending on scope, create:

- `workspace-inventory.md`
- `repository-inventory-<repository>.md`
- `work-item-inventory.md`
- `contributor-aliases.md`
- `chronology-index.md`
- `open-questions.md`

### Detailed work-item files

For every approved item create:

`work-items/<overall-start-date>_<internal-id>_<slug>.md`

Use `unknown-date` if no date is supported.

### Required YAML header for work items

```yaml
---
schema_version: 1
work_item_id: W001
title: Concise title
repositories:
  - repository-name
jira:
  - ABC-123
pull_requests:
  - "123"
implementation_start: 2024-01-15
implementation_end: 2024-02-07
review_end: 2024-02-10
deployment_date: null
date_confidence: High
user_roles:
  - Primary Implementer
overall_confidence: Strongly Supported
generated_at: YYYY-MM-DD
---
```

Use `null` for unknown fields. Do not invent values.

### Work-item body

```markdown
# Title

## Executive summary

## Timeline

## Business and technical context

## Complete work item

## My contribution

## Other contributors

## Technical decisions and trade-offs

## Technologies and competencies

## Outcome

## Evidence map

| Type | Reference | Relevance |
|---|---|---|

## Confidence and uncertainties

## Questions for the user

## Career-value notes
```

## Completion behavior

At the end of every run state:

- phases completed,
- files created or updated,
- work items discovered or analyzed,
- source-code reading performed,
- important limitations,
- recommended next command.

Never continue into a more expensive phase without explicit approval.

## Final principle

Do not analyze Git for its own sake.

Reconstruct the complete engineering story:

Business need  
→ technical challenge  
→ contributors  
→ engineering decisions  
→ implementation  
→ evidence  
→ outcome  
→ user's contribution  
→ career value

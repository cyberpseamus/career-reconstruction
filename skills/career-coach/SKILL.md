---
name: career-coach
description: Transform verified career-reconstruction Markdown reports into CV, LinkedIn, interview stories, positioning options, and a knowledge-refresh plan. Use only after reconstruction reports exist; do not inspect original repositories or source code.
disable-model-invocation: true
argument-hint: "[resume | linkedin | interviews | positioning | refresh-plan | all]"
---

# Career Coach

## Mission

Transform existing evidence-based career reconstruction reports into career-facing material.

This skill must work only from files under:

`career-reports/reconstruction/`

Do not inspect original repositories, Git history, Jira, pull requests, or source code.

If reconstruction reports do not exist or are too incomplete, explain what is missing and recommend `/career-reconstruction`.

## Inputs

Use only:

- workspace and repository inventories,
- work-item inventories,
- detailed work-item files,
- chronology indexes,
- contributor aliases,
- user-confirmed answers,
- open questions.

Inspect `$ARGUMENTS` for the requested output:

- `resume`
- `linkedin`
- `interviews`
- `positioning`
- `refresh-plan`
- `all`

If no goal is supplied, ask the user to choose.

Ask only for materially missing career preferences, such as:

- target role,
- preferred country or market,
- B2B or employment,
- whether leadership roles should be included,
- preferred language,
- desired emphasis such as .NET, architecture, AI, industrial systems, or broad software engineering.

Do not ask for facts already present in the reports.

## Evidence rules

Every career claim must be traceable to at least one reconstruction report.

Distinguish:

- verified facts,
- user-confirmed facts,
- cautious synthesis,
- unresolved gaps.

Never invent:

- metrics,
- team size,
- system scale,
- ownership,
- promotions,
- production outcomes,
- leadership,
- business impact.

Do not copy confidential names into career-facing outputs.

## Positioning principle

Position the user as an experienced engineer whose new direction builds on existing expertise.

Do not present the user as a junior merely because a target technology is newer.

Balance breadth with a coherent professional identity.

Possible positioning may include, when supported:

- Senior .NET Backend Engineer
- Senior Software Engineer
- Backend and Integration Engineer
- Modernization and Migration Specialist
- Enterprise Systems Engineer
- Applied AI Software Engineer in transition
- Industrial or Energy Software Engineer
- Technical Lead experience without a people-management focus

Do not force an AI narrative unless the user requests it and evidence supports the transition story.

## Chronology

Use dates from work-item YAML headers and chronology indexes.

Sort primarily by implementation start.

Preserve overlapping projects and responsibilities.

Distinguish implementation, review, and deployment.

Mark uncertain dates.

Do not infer that one project ended when another began.

## Output directory

Write outputs under:

`career-reports/career-materials/`

Do not modify reconstruction files.

## Deliverable: unified profile

Create `unified-career-profile.md` containing:

1. professional identity,
2. chronological career narrative,
3. core competencies,
4. recurring engineering themes,
5. strongest evidence-backed achievements,
6. responsibility and ownership patterns,
7. collaboration and leadership evidence,
8. technology matrix,
9. plausible target roles,
10. gaps requiring clarification.

For each achievement cite the source work-item filename.

## Deliverable: resume source material

Create `resume-source-material.md`.

Include:

- three professional-summary variants,
- 12–15 evidence-backed achievement bullets,
- concise technology grouping,
- selected project descriptions,
- leadership wording that does not overstate management interest,
- a list of metrics or facts the user could add if known.

Use action-oriented wording, but do not inflate claims.

Avoid generic phrases such as:

- worked on,
- participated in,
- responsible for.

Do not produce a finished one-page CV unless explicitly requested.

## Deliverable: LinkedIn source material

Create `linkedin-source-material.md`.

Include:

- three headline options,
- an About section,
- experience-entry source text,
- suggested skills,
- Featured-section ideas,
- a restrained Open to Work positioning statement.

Keep wording credible and searchable.

Do not describe planned studies or AI competence as completed experience.

## Deliverable: interview story bank

Create `interview-story-bank.md`.

Build 8–12 distinct evidence-based stories.

Use:

- Situation
- Task
- Action
- Result
- Evidence
- Missing detail
- Likely follow-up questions
- Risks or weak spots in the story

Cover, where evidence exists:

- difficult technical problem,
- migration,
- architecture decision,
- performance,
- database work,
- production incident,
- integration,
- collaboration,
- disagreement or trade-off,
- leadership,
- failure or lesson learned.

Do not fabricate a positive result when the outcome is unknown.

## Deliverable: knowledge refresh plan

Create `knowledge-refresh-plan.md`.

Derive preparation topics from actual work.

Group into:

1. knowledge likely present but difficult to articulate,
2. concepts requiring refresh,
3. technologies with shallow or outdated exposure,
4. common senior interview fundamentals absent from project evidence.

Prioritize:

- High
- Medium
- Low

For each topic include:

- why it matters,
- source work items,
- likely interview questions,
- a small practical refresh task.

Do not recommend relearning every technology from scratch.

## Deliverable: positioning options

Create `positioning-options.md`.

Provide no more than four coherent target profiles.

For each include:

- target title,
- concise value proposition,
- supporting evidence,
- missing capabilities,
- immediate credibility,
- six-to-twelve-month development needs,
- risks of the positioning.

Clearly separate:

- roles credible now,
- adjacent roles,
- future pivot roles.

## Deliverable: open questions

Create or update `career-materials-open-questions.md`.

Deduplicate unanswered questions concerning:

- measurable impact,
- scale,
- deployment,
- responsibility boundaries,
- team collaboration,
- design rationale,
- business value,
- lessons learned.

Order questions by potential value for CV or interviews.

## Optional AI pivot assessment

Only when requested, create `ai-pivot-assessment.md`.

Assess how existing experience can transfer into:

- AI-enabled backend engineering,
- applied AI systems,
- LLM integrations,
- RAG and agentic applications,
- MLOps or AI platform engineering,
- industrial or energy AI.

Separate:

- transferable strengths,
- missing foundations,
- portfolio opportunities,
- roles plausible now,
- roles plausible after study and projects.

Do not assume that a course or degree alone creates senior AI experience.

## Quality checks

Before finishing:

1. confirm every major claim has a source,
2. remove duplicates,
3. remove confidential names,
4. flag unsupported metrics,
5. ensure chronology is consistent,
6. ensure contributor work is not attributed to the user,
7. ensure leadership wording is evidence-based,
8. ensure planned skills are not described as acquired,
9. ensure target positioning is coherent,
10. list unresolved uncertainties.

## Completion behavior

At the end state:

- inputs used,
- outputs created or updated,
- strongest evidence themes,
- important gaps,
- recommended next action.

Do not inspect repositories to fill gaps. Use `/career-reconstruction` instead.

## Final principle

Reconstruction establishes facts.

Career coaching turns those facts into a truthful, coherent professional story.

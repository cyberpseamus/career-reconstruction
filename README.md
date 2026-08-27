# Career Reconstruction

Evidence-based career reconstruction for software engineers using Claude Code.

`career-reconstruction` helps reconstruct actual engineering work from development artifacts such as Git history, Jira issues, pull requests, feature branches, and selected source code.

Instead of treating commits as a career history, it reconstructs complete work items and uses them as evidence for understanding what an engineer actually worked on.

A companion skill, `career-coach`, transforms the resulting reconstruction reports into source material for CVs, LinkedIn profiles, interviews, and career positioning.

## Skills

### `career-reconstruction`

Reconstructs engineering work from Software Development Lifecycle artifacts.

It can use:

* Jira issues,
* pull requests,
* feature branches,
* merge commits,
* Git metadata,
* selected diffs and source code.

The primary unit of analysis is a **Work Item**, rather than an individual commit.

The skill is designed to:

* reconstruct work chronologically,
* correlate evidence across multiple sources,
* distinguish the user's contribution from other contributors' work,
* avoid inventing impact or ownership,
* selectively inspect code only when useful,
* produce structured reconstruction reports for later analysis.

It supports multiple analysis depths so that large repositories can first be explored using inexpensive metadata before deeper code analysis is performed.

### `career-coach`

Consumes reports produced by `career-reconstruction`.

It does **not** inspect the original repositories, Git history, Jira, pull requests, or source code.

It can transform reconstruction evidence into:

* CV source material,
* LinkedIn source material,
* interview stories,
* career positioning options,
* knowledge-refresh plans.

Career claims are expected to remain traceable to the reconstruction evidence.

## Why?

After working on many projects for several years, reconstructing what you actually did can be surprisingly difficult.

Git history alone is usually insufficient:

* one feature may involve many commits,
* multiple developers may contribute to the same feature,
* squash merges can hide original authorship,
* Jira, pull requests and branches may contain important context,
* implementation details may only become clear after selectively examining code.

This project treats career reconstruction as an **evidence correlation problem** rather than a commit summarization problem.

A simplified workflow is:

```text
Jira / Pull Requests / Branches / Git / Code
                    │
                    ▼
          career-reconstruction
                    │
                    ▼
        Evidence-based career reports
                    │
                    ▼
              career-coach
                    │
                    ▼
       CV / LinkedIn / Interviews
```

## Installation

Clone this repository:

```bash
git clone https://github.com/cyberpseamus/career-reconstruction.git
```

Copy the skills to your personal Claude Code skills directory:

```bash
mkdir -p ~/.claude/skills

cp -r career-reconstruction/skills/career-reconstruction ~/.claude/skills/
cp -r career-reconstruction/skills/career-coach ~/.claude/skills/
```

The skills should then be available in Claude Code as:

```text
/career-reconstruction
/career-coach
```

Alternatively, they can be installed as project-level skills under:

```text
.claude/skills/
```

## Basic workflow

Start with:

```text
/career-reconstruction
```

The skill will ask for missing information such as:

* repositories to analyze,
* date range,
* user identity in development systems,
* available evidence,
* reconstruction goal,
* desired analysis depth.

Reconstruction reports are written under:

```text
career-reports/
```

After sufficient reconstruction material exists, run:

```text
/career-coach
```

and choose the desired output, such as:

```text
resume
linkedin
interviews
positioning
refresh-plan
```

## Privacy

Career reconstruction may involve sensitive professional information.

Depending on the available evidence, this can include:

* repository names and URLs,
* source code,
* contributor names and email addresses,
* issue tracker identifiers and content,
* customer or product names,
* internal project information.

Review generated reports carefully before publishing or sharing them.

Do not use this project to disclose information that you are not authorized to disclose.

**All examples included in this repository are fictional and are not derived from real employers, clients, repositories, contributors, issue trackers, or internal systems.**

## Project status

This is an early **v0.1** release.

The current goal is to publish and test the existing workflow rather than provide a polished career-management product.

The skills should be considered experimental and their outputs should always be reviewed by a human.

## Repository structure

```text
career-reconstruction/
├── README.md
├── LICENSE
├── .gitignore
├── examples/
│   └── README.md
└── skills/
    ├── career-reconstruction/
    │   └── SKILL.md
    └── career-coach/
        └── SKILL.md
```

## License

MIT

# mySkills

A personal collection of **skills for AI agents**: structured, version-controlled instructions, workflows, and reusable resources.

The goal is to keep my skills available regardless of the computer I work on or the agent I use: Codex, Claude Code, or other compatible agents. This repository is the single source for installing and updating them on every machine.

## Organization

Skills are grouped by domain in top-level folders, with each skill in its own self-contained directory:

```text
mySkills/
├── README.md
├── AGENTS.md
├── LICENSE
├── projectManagement/
│   ├── Notion-Story-Creation/
│   │   ├── SKILL.md
│   │   └── agents/openai.yaml
│   ├── Project-Definition/
│   │   ├── SKILL.md
│   │   └── agents/openai.yaml
│   └── Project-Documentation/
│       ├── SKILL.md
│       ├── agents/openai.yaml
│       └── references/documentation-guide.md
├── softwareDevelopment/
│   ├── story-development-plan/
│   │   ├── SKILL.md
│   │   ├── agents/openai.yaml
│   │   └── references/development-plan.md
│   └── story-development/
│       ├── SKILL.md
│       └── agents/openai.yaml
└── teaching/
    ├── teaching-context/
    │   ├── SKILL.md
    │   └── agents/openai.yaml
    └── teaching-assessment/
        ├── SKILL.md
        ├── agents/openai.yaml
        └── references/onlitest-handoff.md
```

`projectManagement/` contains skills for project documentation, backlog story creation, prototyping, project definition, and related workflows. `softwareDevelopment/` contains skills for planning and implementing stories. `teaching/` contains shared teaching context and assessment preparation workflows. Add other top-level folders as new domains are introduced. Each skill may also include `scripts/`, `references/`, or `assets/` when needed.

Each `SKILL.md` describes the skill's purpose, when to use it, and how to perform the workflow. The format follows the open Agent Skills standard, also used by [Codex](https://learn.chatgpt.com/docs/build-skills).

To keep the collection consistent and portable:

- Write the README and all skills in English, including metadata, instructions, and supporting documentation.
- Write generated artifacts in the language required by their destination project or the user. Notion card titles and bodies follow the project's language; property names and categorical option labels stay in English, including the types `story`, `task`, and `spike` and all status values, both at creation and during later updates.
- Place every skill under its domain folder rather than directly at the repository root.
- Use unique, descriptive skill names.
- Keep instructions and required resources together, using relative paths.
- Document required tools, dependencies, and any operating system or agent limitations.
- Do not include credentials, secrets, or machine-specific paths.

## Available skills

| Domain | Skill | Purpose |
| --- | --- | --- |
| Project management | [Notion-Story-Creation](projectManagement/Notion-Story-Creation/SKILL.md) | Create Notion cards as stories with named scenarios or standalone AC blocks and GIVEN/WHEN/THEN/AND clauses, spikes with expected outputs, or tasks with to-do lists. |
| Project management | [Project-Definition](projectManagement/Project-Definition/SKILL.md) | Refine ideas through a critical interview with explicit scope and depth, then offer a documentation handoff. |
| Project management | [Project-Documentation](projectManagement/Project-Documentation/SKILL.md) | Continue refinement while updating concise, contextual documentation in Notion or an existing repository. |
| Software development | [Story Development Plan](softwareDevelopment/story-development-plan/SKILL.md) | Interactively plan one story as reviewable increments with clear completion criteria and resumable state. |
| Software development | [Story Development](softwareDevelopment/story-development/SKILL.md) | Implement and resume a story one approved increment at a time, keeping the development plan and source card status current. |
| Teaching | [Teaching Context](teaching/teaching-context/SKILL.md) | Resolve School in Notion and retrieve concepts, lessons, and assessments for specialized teaching workflows. |
| Teaching | [Teaching Assessment](teaching/teaching-assessment/SKILL.md) | Collaboratively prepare practical assessments with increasing difficulty, a common route to 6/10, and an evaluation table. |

The portable identifiers match the `name` fields in each `SKILL.md`: `notion-story-creation`, `project-definition`, `project-documentation`, `story-development-plan`, `story-development`, `teaching-context`, and `teaching-assessment`. The Notion workflows require access to the target project or teaching area through a Notion connector or equivalent integration; documentation and development in a repository require access to that repository and its relevant tools.

Teaching Context is the shared dependency for teaching workflows. The teacher has confirmed that School is the Notion wiki titled Scuola; the skill records its verified root and data source and discovers the current hierarchy for concepts, lessons, and assessments without assuming database names. Teaching Assessment requires this skill alongside it. It asks for missing subject and topics, retrieves the relevant lessons, and requests material directly from the teacher when lessons cannot be found. It then enters native plan mode autonomously when the host permits it and designs the assessment interactively. If the agent cannot switch modes, it explains the limitation and waits for the teacher to activate native plan mode; a host without that mode cannot run the workflow as specified.

Assessments use one common version and common mastery criteria while preserving teacher-supplied access arrangements, including those in a PDP. Preliminary theory plus one very simple practical exercise provides the route to 6/10; progressively harder practical tasks provide evidence for higher grades. Practical work dominates points and expected time. Every assessment includes an evaluation table and an explicit grade conversion, preferably with a total score that is a multiple of 10. Generated assessments follow the teacher's or destination project's language.

Teaching Assessment explicitly asks whether to use Onlitest. If selected, it proposes a self-contained, copy-ready template for the Onlitest chatbot with the agreed tasks, taught scope, scoring, correction key, and delivery constraints. Planning also resolves the actual Verifiche destination and maps assessment metadata to its current Notion properties. Moving from the agreed plan to implementation includes creating and verifying the assessment page in Verifiche, with applicable writable properties correctly populated, without a separate save approval. The page also contains the chatbot handoff when selected; creating or publishing an assessment in Onlitest itself requires a separate request.

Backlog cards stay minimal throughout development. Stories and tasks retain their brief description and AC or to-do list; development plans, redirects, progress, and handoff state stay outside the card. A completed spike contains only a concise Output section summarizing the result. If its deliverable is other cards, that section contains only links to the cards created.

Story Development manages the source card's status as part of execution, using the destination's existing English workflow values without separate approval for each transition. Planning preserves the current status; authorized implementation activates the card; final pending review and concrete blockers use matching statuses when available; completion requires all work, checks, and applicable final approval. Individual step checkpoints do not complete the whole card. Saved transitions are verified, and unavailable or failed tracker updates remain explicit in the resume state.

When the development plan is already displayed in a side panel or connected document, both development skills update that same artifact through supported host tools and verify the saved changes. Progress updates and substantive revisions to an existing plan happen on the go in the current mode, without requiring re-entry into plan mode; material scope changes and execution remain subject to the applicable approvals. If the displayed artifact cannot be updated, the workflow explicitly reports the synchronization gap and supplies the current plan in the conversation.

Project-Definition asks for analysis depth before substantive questions and establishes a precise scope. Both project skills ask before changing either boundary. Once the idea is sufficiently defined, Project-Definition asks whether to begin documentation and, if accepted, hands the current context to Project-Documentation. The latter first resolves where to save, reads existing context, and updates canonical documentation using local conventions. Specialized deliverables go to suitable available skills.

These workflows are inspired by Matt Pocock's [grill-me](https://github.com/mattpocock/skills/blob/main/skills/productivity/grill-me/SKILL.md) and [grill-with-docs](https://github.com/mattpocock/skills/blob/main/skills/engineering/grill-with-docs/SKILL.md), with explicit scope and depth controls and a separate documentation phase. They do not require those upstream skills to be installed.

For implementation, Story Development uses native plan mode for initial planning when no development plan exists. If the host does not allow the agent to switch modes, it explains the limitation and waits for the user to activate native plan mode for initial creation; if that mode is unavailable, initial planning cannot proceed as specified. Existing plans are reconciled and revised in the current mode, including on resumption and during implementation, without requiring another switch to plan mode. Existing explicit execution authority remains valid, while plan revisions do not grant additional execution authority. The plan is built interactively; a stored document is optional. Each step has a logical outcome, completion criteria, verification evidence, and a review checkpoint. By default, the user must approve each increment before the next begins. Explicit permission for the next N steps or autonomous story completion changes that boundary only within the granted scope. The plan tracks changes, approvals, evidence, and remaining work and is returned in full at checkpoints so it can be pasted into another chat. Source changes must also be available in the resumed checkout.

## Install everything with one command

Use the open source [Skills CLI by Vercel](https://github.com/vercel-labs/skills). It requires **Node.js 22.20 or later**, with npm/npx available. Git sources also require Git and access to the repository.

Run this from any directory on the machine where you want to install the skills:

```sh
npx --yes skills add frankox/mySkills --global --all
```

As described in the [command documentation](https://github.com/vercel-labs/skills/blob/main/docs/commands.md), `--global` installs for the current user, and `--all` selects every skill and every supported agent without interactive prompts. There is no need to write a separate installer for each agent.

To install every skill for Codex and Claude Code only:

```sh
npx --yes skills add frankox/mySkills --global --skill '*' --agent codex claude-code --yes
```

If the repository is private, Git access must already be configured on the new machine. You can use the SSH address directly:

```sh
npx --yes skills add git@github.com:frankox/mySkills.git --global --all
```

## Install from a local checkout

To install local changes before publishing them, run this from the repository root:

```sh
npx --yes skills add . --global --all
```

## Verify and update

To list globally installed skills:

```sh
npx --yes skills list --global
```

After publishing changes or new skills, rerun the installation command on each machine. For a local checkout, update it with `git pull` first, then repeat the installation from `.`. Synchronization between computers is not automatic.

## What “available everywhere” means

Global installation makes skills available across the current user's projects, in the locations expected by supported agents. For example, Codex reads personal skills from `~/.agents/skills/` and supports symbolic links, as described in the [official documentation](https://learn.chatgpt.com/docs/build-skills).

Portability has two requirements: the agent must support the skill format, and the machine must have the tools required by each skill. A skill that uses an external service or a specific tool also requires that setup. The command installs skills, but it does not install agents, configure accounts or services, or automatically make unsupported agents compatible.

## License

[MIT](LICENSE).

---
name: notion-story-creation
description: Create or draft Notion project backlog cards as stories, tasks, or spikes with fixed structures, project-language content, and clarification of any uncertainty before execution. Use when a user asks to turn requirements or activities into Notion cards.
---

# Notion-Story-Creation

Create concise, actionable Notion cards using exactly one type: `story`, `task`, or `spike`. Keep property names and categorical option labels in English, including card types and status names and values. Write the title and body in the language of the destination Notion project.

## Resolve context before execution

1. Identify the target project and destination page or database from the request and available Notion context. Use the available Notion connector or equivalent integration to read the project, relevant requirements, representative existing cards, and destination properties and allowed values. Do not hardcode workspace IDs, property names, or tool names.
2. Establish the project's language from its documented convention or consistent existing project content. Write the card title, description, headings, scenario text, acceptance criteria, expected outputs, and checklist in that language. Follow existing conventions for labels such as AC and Given/When/Then. Property names and categorical option labels must remain in English regardless of the project's language; use `story`, `task`, and `spike` for card types. Preserve proper names, literal identifiers, and relation targets; do not translate free-text content merely because it is stored in a property. Do not infer the project language solely from the user's message or these English instructions.
3. Determine the type using the rules below. If the request does not make the type clear, ask the user to choose `story`, `task`, or `spike`.
4. Resolve every remaining uncertainty before execution. Ask concise questions about anything ambiguous, missing, or contradictory, including destination, language, scope, behavior, criteria, expected output, or database mapping. Read-only investigation may continue, but do not create or modify a card, or finalize a draft based on unresolved assumptions. If project context is inaccessible, ask for access or the missing information rather than guessing.

Once the context is clear and creation has been requested, proceed without requiring an additional routine confirmation. A request for a draft authorizes drafting only.

## Choose exactly one type

| Type | Meaning | Required body |
| --- | --- | --- |
| `story` | A change that delivers a direct benefit to the user. | Brief problem description and an AC section using Given/When/Then. |
| `task` | Useful or necessary work that does not directly benefit the user, such as internal maintenance or technical enablement. | Brief description of the activity and the problem it solves, followed by a to-do checklist. |
| `spike` | An investigation intended to resolve uncertainty or support a decision. | Brief description of what must be investigated, followed by the expected output. |

Respect an explicitly requested type. If it conflicts with the described work, ask before proceeding. Do not treat every request called a “story” or “card” as type `story`; these terms may refer generically to backlog items. Do not use hybrid types or silently split a request into multiple cards.

## Story structure

- Keep the description short but sufficient to explain the problem and intended user benefit. Include the actor when established by the requirements.
- Include an **AC** section with observable, testable acceptance criteria in Given/When/Then form. Avoid implementation instructions masquerading as user outcomes.
- Prefer scenarios whenever criteria share the same initial context: state the scenario's **Given** once, then list its criteria as **When/Then** pairs. A **Then**-only criterion is valid when the trigger is already unambiguous from the scenario or a preceding criterion; do not rely on an unstated action.
- Use a new scenario when the initial context changes. If grouping adds no clarity, use standalone complete Given/When/Then criteria instead.
- Include relevant alternative or failure behavior only when supported by the requirements. Ask about unresolved behavior rather than inventing it.

Structural template; replace every placeholder and adapt all card text to the project's language:

```markdown
## Description
[Brief problem description and intended user benefit.]

## AC

### Scenario: [Scenario name]
**Given** [Shared initial context.]

1. **When** [An action or event], **Then** [An observable result].
2. **Then** [Another observable result under the same context and established trigger].
3. **When** [Another action or event under the same initial context], **Then** [Its observable result].
```

Use only the scenarios and criteria needed for the actual request; the template does not prescribe a fixed count.

## Spike structure

Keep the description focused on the uncertainty or question being investigated. Follow it with the expected output: a concrete deliverable such as a comparison, findings, a feasibility result, a prototype with documented findings, or a recommendation. Specify what the output must answer without presuming the investigation's conclusion.

```markdown
## Description
[Brief investigation context and question to resolve.]

## Expected output
[Concrete deliverable and the questions it must answer.]
```

Do not add an AC section or a task checklist to a spike.

## Task structure

Briefly explain the activity and the problem it solves or why it is necessary. Follow the description with a checklist of concrete, verifiable actions. Keep the work within the established scope.

```markdown
## Description
[Brief explanation of the activity and the problem it solves.]

## To-do
- [ ] [Concrete action.]
- [ ] [Another required action, if applicable.]
```

Do not replace the task checklist with user-facing acceptance criteria.

## Keep cards minimal throughout their lifecycle

Cards are quick-reading backlog items, not development journals or resumable plans. Apply these rules when creating a card and pass them to any planning, implementation, or documentation workflow that continues the work:

- **Story and task:** preserve the brief description and AC or to-do list. During development, edit only what an agreed change to requirements makes necessary; update existing checklist items or properties when tracker updates are authorized. Do not append progress reports, redirects, intermediate decisions, implementation steps, test logs, approval history, or handoff snapshots.
- **Spike before completion:** use the investigation question and expected output above to define the work. Keep interim analysis in the conversation or a separately requested analysis document, not in the card.
- **Completed spike:** replace the investigation brief and expected output with a single **Output** section containing only a short summary of the analysis result, including the conclusion or recommendation and any limitation essential to interpreting it. Do not retain the investigation process or intermediate findings. If the deliverable is other cards, the body must contain only **Output** and links to the cards actually created; do not duplicate their content or add an analysis narrative. Translate the heading to the project's language.

Update an existing section in place rather than appending another summary. A workflow transition, redirect, tool action, or plan revision is not a reason to modify the card. A request to create a card does not authorize future tracker updates or creation of additional output cards.

## Create and verify the Notion card

1. Prepare a short, specific title and the body for the selected type. Keep the required sections concise; do not add unrelated sections by default.
2. Set the type explicitly using the destination's English type property and the option `story`, `task`, or `spike`. Reuse existing English property names and option labels, preserving their capitalization. If the schema uses non-English property names or categorical labels, lacks a suitable option, or has an uncertain mapping, resolve the English schema change with the user before writing; do not silently retain localized labels, create duplicate properties, or rename shared database fields. For a destination without database properties, use an explicit English type label.
3. Use the established project relation or parent destination. Set additional properties only when supplied by the user or unambiguously established by project conventions. The status property name and every status option must be in English, regardless of the project's content language; reuse the destination's existing English workflow values rather than inventing a new workflow. Apply this rule to later status transitions as well as creation. Resolve non-English status schema labels as described above before writing. Do not invent an owner, priority, status, estimate, or deadline.
4. Create the card only after all uncertainties are resolved. Use native headings and checkboxes when supported. If a matching card already exists and the intended action is unclear, ask before duplicating or updating it.
5. Verify the resulting card's destination, title, explicit English type, English property names and categorical labels, project-language content, required body sections, and checklist or AC formatting. If a write returns an uncertain result, check whether it succeeded before retrying to avoid duplicates.
6. Return the card link and its type, and report any verification failure accurately. For draft-only work, return the title, explicit type, and formatted body without creating a Notion page.

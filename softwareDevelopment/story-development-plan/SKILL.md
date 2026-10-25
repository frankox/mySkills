---
name: story-development-plan
description: Interactively plan implementation of a specific story before coding. Retrieve story and repository context, question unresolved decisions, and produce a resumable development plan with reviewable increments, completion criteria, and explicit execution approvals. Use for planning, not implementation.
---

# Story Development Plan

Turn one story into a development plan the user can understand, review, change, and resume in another chat. Use a critical interview with a continuously updated plan as its document. Do not implement the story while planning.

## Establish the story and repository

1. First ask which story to work on unless its text or an unambiguous reference is already provided. Accept pasted content or an accessible card, issue, or document. Do not substitute a guessed story or silently create one.
2. Fetch the full story and relevant linked context when available. Recover its problem, scope, acceptance criteria, constraints, and exclusions. Identify the target repository; ask if it is ambiguous or inaccessible.
3. Read applicable repository instructions, architecture and domain documentation, relevant source code, nearby tests, dependency versions, and build or validation conventions. Inspect the working tree to distinguish existing work from the proposed changes. Retrieve only context needed for this story.
4. Discover and read applicable repository or technology skills. Resolve factual questions from accessible sources before asking the user. Where local guidance is insufficient, consult official documentation appropriate to the actual technology version. Do not invent APIs or replace repository conventions with generic preferences.
5. If a supplied plan already exists, recover it and compare its story, code state, decisions, and unfinished work with current evidence. Preserve valid decisions and progress instead of restarting discovery.

Use the source card's acceptance criteria as the basis for coverage. If it is a task or spike, use its checklist or expected output instead of fabricating user-story AC. Ask about missing or contradictory requirements that affect implementation.

## Plan interactively within this story

Use the host's native plan mode when available. If it cannot be activated by the agent, explain that the session remains planning-only and keep the plan in the conversation or available planning surface. Do not claim a mode switch that did not happen. No physical document, Notion page, or repository plan file is required; create one only if requested, following its destination's conventions.

- State the story-specific objective and exclusions. The analysis depth is implementation planning for this story, not general project exploration.
- Ask the questions needed to settle behavior, implementation choices, dependencies, relevant edge cases, and validation. Usually ask one focused question at a time; group up to three independent questions when useful. Wait for decisions before dependent follow-ups.
- Challenge weak assumptions and contradictions. Offer a reasoned recommendation or useful options without treating an unanswered proposal as agreement.
- Keep the plan current as answers settle decisions. Distinguish confirmed requirements, proposed choices, accepted assumptions, blockers, and deferred questions.
- When the discussion moves beyond the story or into unnecessary detail, identify the boundary and ask whether to revise scope or return to the current story. Do not expand scope while that choice is pending.
- Stop questioning when the scoped implementation can be planned reliably. Do not require unrelated architectural decisions or an exhaustive design.

## Design reviewable increments

Read [the development plan format](references/development-plan.md) before producing the plan. Start with a brief description, then a sequence of incremental steps; include the compact state needed to resume work.

Each step must have:

- A stable identifier, a clear outcome, and an understandable boundary in the code.
- A link to the AC, task item, expected output, or necessary enabling work it addresses.
- Explicit completion criteria and a proportionate verification method.
- Relevant prerequisites and a review point that lets the user understand what changed and why.

Prefer coherent behavior changes that include their relevant implementation and verification. Split steps when their combined behavior or diff would be difficult to review. Combine trivial edits when separating them would create ceremony without a useful checkpoint. Do not prescribe a fixed step count or turn each file, import, or command into a separate step.

Completion can be established by observable AC coverage, meaningful automated tests developed for that increment, an appropriate existing check, or explicit user acceptance when objective verification is impractical. State which evidence is required. Do not promise test-driven development, require new tests for every trivial change, or use tests that merely mirror the implementation.

Make the approval boundary explicit: technical completion alone does not authorize the next step. By default, each completed increment requires the user's approval before proceeding.

## Agree on execution and hand off

Present the complete current plan and resolve implementation-blocking questions. Ask the user to approve the plan and authorize the first identified step. They may approve the plan without authorizing execution; keep those decisions distinct. A clearly worded combined approval may cover both.

When execution is authorized, use `story-development` if available, passing the story, repository context, current plan, decisions, evidence, and exact authorization. Use the host's skill mechanism or locate and read its installed instructions. This is a workflow transition in the current conversation, not a new chat or a delegation request. If that skill is unavailable, provide the plan and explain that execution has not been handed off.

Do not infer permission to finish the story from approval of a single step. Record any explicit grant to complete specified steps or the remaining story, including its limits, so execution can enforce it.

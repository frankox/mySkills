---
name: story-development-plan
description: Interactively plan implementation of a specific story before coding. Retrieve story and repository context, question unresolved decisions, and produce a resumable development plan with reviewable increments, completion criteria, and explicit execution approvals. Use for planning, not implementation.
---

# Story Development Plan

Turn one story into a development plan the user can understand, review, change, and resume in another chat. Use a critical interview with a continuously updated plan as its document. Do not implement the story while planning.

When the user requests teacher mode or learning-focused pairing, use the available `story-learning` skill to add functional and learning objectives and user-driven increments to this plan. Carry that mode and its driver boundary into implementation; do not restart an existing card or assume the user's real experience is junior.

## Use native plan mode for initial creation

When no development plan exists, enter the host's native plan mode before creating it, using its supported mode-switch mechanism when available. Activate it autonomously when possible. If the agent cannot switch modes, explain the limitation and ask the user to activate native plan mode for initial creation; wait for the host to confirm it is active. Do not claim a switch that did not happen or bypass host controls. If native plan mode is unavailable, explain that initial planning cannot proceed as specified.

When updating an existing plan, work in the current mode, including outside plan mode during implementation. Do not require a mode switch to clarify decisions, revise steps, dependencies, scope proposals, or verification, or reconcile a resumed plan. Resolve material scope changes and execution permissions with the user in the current conversation before affected implementation. Update the same displayed plan when supported. If the displayed plan cannot be updated during implementation, follow the end-of-step synchronization fallback in `story-development`: report the pending changes and ask the user to activate native plan mode. Do not assume an autonomous mode switch is available or claim one without host confirmation.

## Establish the story and repository

1. First ask which story to work on unless its text or an unambiguous reference is already provided. Accept pasted content or an accessible card, issue, or document. Do not substitute a guessed story or silently create one.
2. Fetch the full story and relevant linked context when available. Recover its problem, scope, acceptance criteria, constraints, and exclusions. Identify the target repository; ask if it is ambiguous or inaccessible.
3. Read applicable repository instructions, architecture and domain documentation, relevant source code, nearby tests, dependency versions, and build or validation conventions. Inspect the working tree to distinguish existing work from the proposed changes. Retrieve only context needed for this story.
4. Discover and read applicable repository or technology skills. Resolve factual questions from accessible sources before asking the user. Where local guidance is insufficient, consult official documentation appropriate to the actual technology version. Do not invent APIs or replace repository conventions with generic preferences.
5. If a supplied plan already exists, recover it and compare its story, code state, decisions, and unfinished work with current evidence. Preserve valid decisions and progress instead of restarting discovery.

Use the source card's acceptance criteria as the basis for coverage. If it is a task or spike, use its checklist or expected output instead of fabricating user-story AC. Ask about missing or contradictory requirements that affect implementation.

## Plan interactively within this story

Keep native plan mode active while creating the initial plan. Try to revise an existing plan on the go in the current mode; request plan mode at the end of the implementation step when the displayed plan cannot be synchronized. No physical document, Notion page, or repository plan file is required; create one only if requested, following its destination's conventions.

If the plan already exists in a side panel, canvas, or connected document, read and update that same artifact through the host's supported editing tool instead of maintaining a divergent chat-only copy. Preserve user edits and verify each saved update. Keep its artifact identity and latest verified revision in the resume state when available, and pass them to `story-development` so execution updates the same plan after leaving plan mode. If the artifact is unavailable or cannot be edited, record pending changes and provide the current plan in the conversation; do not claim that a chat response updated the side view. Pass the pending synchronization state to implementation. At its next step boundary, the implementation workflow must notify the user and ask them to activate native plan mode, even under broader execution authority. Once plan mode is confirmed, publish the complete revised native plan using the host-required proposed-plan format; do not treat a native plan document as an editable canvas.

Keep this working plan separate from the source card, even when both are in Notion. Plan revisions, redirects, decisions, and handoff snapshots do not belong in the card. If card updates are authorized, limit story/task changes to necessary agreed requirement corrections while preserving their minimal description and AC or to-do list. Keep interim spike analysis outside the card; on completion, its body contains only a concise Output section with the result, or only links to created cards when those are the deliverable. Pass these boundaries to the implementation workflow.

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
- An explicit current status: `planned` (to do), `in_progress`, or `completed` (done), with the additional review, blocked, and superseded states defined in the plan format when applicable. Never leave a step's status implicit or track only the active step.

Include a compact progress table listing every step ID, outcome, and current status before the detailed increments. Initialize unstarted steps as `planned`; for resumed work, recover statuses from the actual code, evidence, and review decisions. Keep this table synchronized with the detailed steps throughout implementation and in every full plan snapshot. Render human-facing labels in the user's or project's required language.

Prefer coherent behavior changes that include their relevant implementation and verification. Split steps when their combined behavior or diff would be difficult to review. Combine trivial edits when separating them would create ceremony without a useful checkpoint. Do not prescribe a fixed step count or turn each file, import, or command into a separate step.

Completion can be established by observable AC coverage, meaningful automated tests developed for that increment, an appropriate existing check, or explicit user acceptance when objective verification is impractical. State which evidence is required. Do not promise test-driven development, require new tests for every trivial change, or use tests that merely mirror the implementation.

Make the approval boundary explicit: technical completion alone does not authorize the next step. By default, each completed increment requires the user's approval before proceeding.

## Agree on execution and hand off

Present the complete current plan and resolve implementation-blocking questions. Ask the user to approve the plan and authorize the first identified step. They may approve the plan without authorizing execution; keep those decisions distinct. A clearly worded combined approval may cover both.

When execution is authorized, use `story-development` if available, passing the story, repository context, current plan, decisions, evidence, and exact authorization. Use the host's skill mechanism or locate and read its installed instructions. This is a workflow transition in the current conversation, not a new chat or a delegation request. If that skill is unavailable, provide the plan and explain that execution has not been handed off.

Do not infer permission to finish the story from approval of a single step. Record any explicit grant to complete specified steps or the remaining story, including its limits, so execution can enforce it.

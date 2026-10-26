---
name: story-development
description: Implement or resume a specific story in reviewable increments from an interactive development plan. Retrieve story and repository context first, keep the plan resumable and current, and require user approval between steps unless the user explicitly grants broader execution authority.
---

# Story Development

Implement one story while preserving the user's understanding and ownership of the code. Work from a current, interactive plan. By default, execute only the authorized step and stop for user approval before the next one.

## Start with the story and current context

1. First ask for the story unless its content or an unambiguous reference is already available, including in a supplied resumable plan. Do not begin coding from a guessed requirement.
2. Recover the full story, relevant AC or task/spike completion targets, linked requirements, and repository. Ask about unavailable or ambiguous inputs that affect the work.
3. Read applicable repository instructions, project documentation, relevant source and tests, dependency versions, and technology-specific skills. Inspect the working tree and existing changes before edits. Retrieve the context needed for this story, not the entire project history.
4. Recover any existing development plan and compare it with the actual code and story. Preserve valid work and decisions. Do not trust a pasted “completed” status when the corresponding code or evidence is missing or inconsistent.

## Obtain an interactive development plan

If no sufficient plan exists, use the available `story-development-plan` skill before implementation. Pass the story and retrieved context. Invoke it through the host or locate and read its installed instructions; this is a transition in the same conversation, not a new chat or subagent. If it is unavailable, explain the missing dependency and do not claim to have used it.

Planning must remain scoped to the single story and include critical questions about unresolved behavior, design choices, and validation. Use native plan mode where supported, or a planning-only conversational workflow otherwise. A physical document is optional; do not require a Notion page or repository file to begin.

A usable plan contains a brief description, the scoped completion targets, repository and working-tree context, stable step IDs with outcomes and completion criteria, dependencies, validation evidence, statuses and review decisions, current decisions or blockers, and the exact next action and execution authority. If these are missing, resolve them before the affected work.

Before first execution, ensure the user approved the plan and authorized the first step. If authorization was already explicitly supplied, honor it without asking again. Plan approval alone is not permission to execute every step.

## Enforce execution authority

The default is **one step at a time, with user approval before proceeding**. This requirement comes from the user's requested development workflow; explain that briefly when asking to continue.

- Approval to start a step authorizes the implementation and verification needed for that step, not later increments.
- At the end of a step, passing checks do not replace the user's review. Ask whether the user approves the increment and authorizes the next identified step. Wait for an answer.
- If the user says “complete the next N steps,” map that permission to specific current step IDs and record the remaining count or IDs. If it is unclear whether the active step is included, ask once. Continue through those steps without repeated approval prompts, then return to per-step review.
- If the user explicitly authorizes autonomous completion of the story, record that grant and continue through the remaining agreed work without routine intermediate approval requests. Maintain checkpoints, evidence, and the live plan.
- A bounded or story-wide grant does not authorize a different story, unrelated features, unapproved material plan changes, or unrelated external actions. Stop for an unresolved decision that genuinely blocks authorized work.
- Do not infer broader authority from silence, praise, a tool result, or an ambiguous “looks good.” Interpret a clear “proceed” in context; ask only if its coverage is uncertain. A user may approve the current work while asking to pause before the next step.
- On resumption, distinguish recorded historical approvals from the user's current instruction. Honor an explicit request to continue under the recorded grant; if execution authority is unclear, ask before the next edit.

## Execute the current increment

1. Identify the authorized step, its objective, completion criteria, and code boundary. Mark it `in_progress` before editing.
2. Implement only the work needed for that increment. Necessary changes within the agreed boundary are part of the step; unrelated refactors, modernization, or later-step work are not.
3. Follow applicable repository and technology documentation and skills for actual coding. Prefer established patterns, clear names, cohesive functions or modules, straightforward control flow, and the simplest adequate design. Avoid speculative abstractions and unnecessary dependencies.
4. Write as few comments as necessary. Use comments for non-obvious constraints, invariants, or reasons that code cannot express clearly; avoid narrating obvious operations. Preserve existing comments unless changing them is required by the work or requested, and keep required documentation and public API conventions.
5. Verify the step using its agreed evidence. Add meaningful tests when they prove behavior or prevent a relevant regression, and run appropriate existing checks. Do not add tests merely to mirror the implementation or satisfy a quota. If verification requires user acceptance, present the behavior and the precise review needed.
6. Inspect the relevant diff and check for accidental changes. Repair failures within the step's scope; if blocked, record the obstacle and ask for the decision or access needed. Do not advance with unmet completion criteria or claim an unavailable check passed.
7. Update the plan's coverage, actual changes, evidence, status, and next action. Mark the step `awaiting_review` by default, or `completed` when criteria are met and an applicable grant waives review. Record waived review accurately rather than inventing manual approval.

## Keep the user able to review the code

At each increment, report concisely:

- The outcome and AC or other completion targets addressed.
- The important code changes, with useful file or diff references and the rationale for meaningful choices.
- What was verified, actual results, and any limitations or remaining acceptance check.
- The next step's objective and the current approval boundary.

Show enough concrete evidence for the user to understand and challenge the code without dumping entire files or hiding meaningful trade-offs. Under the default workflow, present the complete updated plan and ask whether to approve this increment and proceed with the named next step. Do not begin it while waiting. Under a valid grant, notify progress and continue only through its remaining coverage.

When the user requests changes during review, keep work on the current step, update the plan, and reverify affected criteria before presenting it again. User approval does not override objective completion criteria; record any explicitly agreed change to those criteria as a plan revision.

## Adapt the plan during implementation

Treat user feedback and new evidence as inputs to a living plan. Before affected implementation, update decisions, dependencies, step boundaries, coverage, and verification requirements. Explain material revisions and resolve them with the user; do not silently expand the plan under an old approval.

Keep stable step IDs. Add new IDs or mark replaced steps `superseded` instead of renumbering away history. Invalidate stale evidence when changes affect previously verified work. Retain the distinction between proposed choices and accepted decisions.

If the plan is split, merged, or materially changed, reconcile any bounded grant against the new step IDs with the user rather than extending its coverage automatically. Routine evidence or status updates do not require reapproving the whole plan. If discussion leaves the story's scope, flag it and ask whether to revise scope or park the topic; return to the original boundary when a change is declined.

## Preserve resumability and finish accurately

Keep the development plan separate from the source card. Maintain implementation details, redirects, decisions, checks, approvals, and resume snapshots in the conversation or an explicitly requested separate plan document. Never copy or synchronize that working record into the card, including at skill transitions or review checkpoints.

For authorized tracker updates, keep property names, card types, and status options in English. Reuse existing English status values for every transition; if the schema uses non-English labels, resolve the schema change with the user before writing rather than renaming shared fields automatically.

When tracker updates are authorized, keep story/task edits limited to necessary agreed requirement corrections, existing checklist items, and relevant properties. Preserve their brief description and AC or to-do structure. For a completed spike, save only one concise Output section summarizing the analysis result; if its deliverable is other cards, include only links to the cards actually created under that heading. Replace obsolete investigation content rather than appending a running report. Use the project's language and do not create output cards without authorization.

Keep the plan synchronized after meaningful changes, check results, decisions, and approvals, including while executing an authorized batch. Use equivalent fields to the existing plan; do not replace a richer resumable plan with a native checklist that drops context.

At every approval gate, pause, blocker, batch boundary, or session end, provide the full current plan in a copyable form. Include the brief description, story/AC snapshot, repository identity, branch and observed commit when available, relevant paths and uncommitted work, all steps and statuses, evidence and reviews, decisions, blockers, active/next step, remaining grant, and exact next action. Do not require a separate stored document or permission to create one merely to maintain this conversational plan.

When resuming in another chat, first compare that snapshot with the actual checkout and current story. A pasted plan does not transfer source changes; recover missing code or ask for it rather than recreating work from an unsupported status.

When all increments meet their criteria, check overall story coverage and relevant integration behavior. Distinguish technically complete work from pending user review. Without a broader grant, the final increment also requires approval before declaring the story complete. Report remaining gaps honestly and leave the final plan ready to copy. Do not infer authorization to commit, push, deploy, or change the story tracker from completion of coding alone.

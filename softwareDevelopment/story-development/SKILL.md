---
name: story-development
description: Implement or resume a specific card with repository analysis and a critical requirements interview, then execute reviewable increments with a development plan unless the user explicitly requests no plan. Keep the source card status current and require approval between steps unless broader execution authority is granted.
---

# Story Development

Implement one card while preserving the user's understanding and ownership of the code. Analyze the context and resolve material decisions before coding, whether or not a plan is requested. Normally work from a current, interactive plan; honor an explicit request to develop without one. By default, execute only the authorized increment and stop for user approval before the next one.

If the user requests teacher mode or learning-focused pairing before or during the card, use the available `story-learning` skill in this conversation. Preserve the existing plan, work, and approvals; adapt the plan for learning and follow its user-as-driver boundary instead of implementing code autonomously. Act as the navigator: break each plan step into smaller conceptual and architectural decisions, discuss responsibilities and constraints, and let the user design and write the implementation. Do not dictate snippets, patches, pseudocode, or exact edits unless explicitly requested; requests for clarification or more detail alone do not request code. Apply this boundary throughout execution, debugging, and review. Ordinary questions about the code do not activate teacher mode by themselves.

## Initial planning and mode controls

When no development plan exists and the user has not requested development without a plan, enter the host's native plan mode before creating the initial plan, using its supported mode-switch mechanism when available. If the agent cannot switch modes, explain the limitation and ask the user to activate it for initial planning. Do not claim a switch that did not happen or bypass host controls. If native plan mode is unavailable, explain that initial planning cannot proceed as specified.

When a plan already exists, including on resumption or transition from `story-development-plan`, reconcile it with the current story, checkout, and execution authority in the current mode. First try to update that plan autonomously in the current mode; if the displayed plan cannot be updated, apply the end-of-step fallback below. During execution, update it on the go as feedback and evidence arrive, including changes to decisions, dependencies, step boundaries, and verification methods. Plan editing and execution approval are separate: a revision does not authorize additional work.

After initial planning, use the host's supported transition to implementation once the plan is usable and execution is authorized; explain any required user action to leave plan mode. Honor existing explicit execution authority without requesting it again. Do not assume that the agent can switch modes. Use a mode-switch mechanism only if the host actually exposes one; otherwise ask the user when a switch is needed. Higher-priority mode restrictions always apply.

## Start with the story and current context

1. First ask for the story unless its content or an unambiguous reference is already available, including in a supplied resumable plan. Do not begin coding from a guessed requirement.
2. Recover the full story, relevant AC or task/spike completion targets, linked requirements, and repository. Ask about unavailable or ambiguous inputs that affect the work.
3. Read applicable repository instructions, project documentation, relevant source and tests, dependency versions, and technology-specific skills. Inspect the working tree and existing changes before edits. Retrieve the context needed for this story, not the entire project history.
4. Recover any existing development plan and compare it with the actual code and story. Preserve valid work and decisions. Do not trust a pasted “completed” status when the corresponding code or evidence is missing or inconsistent.

## Analyze and interview before implementation

Apply a critical, adaptive interview inspired by [grill-me](https://github.com/mattpocock/skills/blob/main/skills/productivity/grill-me/SKILL.md) before preparing a plan and before coding without a plan. The procedure here is self-contained; it does not require an upstream skill. A request to skip the plan removes the planning artifact, not analysis or necessary questions.

- Investigate the actual repository, card, documentation, tests, and existing behavior first. Establish facts through available sources; do not ask the user to research something the agent can inspect. Keep read-only investigation moving while awaiting independent user decisions.
- Map the material decisions and their dependencies. Identify which questions can be answered now and which depend on an unresolved choice or missing evidence. Do not choose downstream behavior based on an answer the user has not given.
- Ask focused questions in successive rounds, usually one at a time or up to three independent questions together. Explain why each matters and offer a recommendation with concrete trade-offs when useful. Wait for answers before dependent questions or implementation; a recommendation is not agreement.
- Probe the actual objective, observable behavior, exclusions, responsibilities, interfaces, data constraints, relevant failure cases, dependencies, and acceptance evidence as needed for this card. Challenge contradictions and weak assumptions constructively. Ask for concrete examples when abstract wording hides different interpretations. These are areas to investigate, not a mandatory questionnaire for every task.
- After each answer, update the shared understanding and follow its consequences until material choices are settled. Record accepted decisions separately from proposals, assumptions, and deferred questions. Do not repeat settled questions unless new evidence conflicts with them or reopen completed discovery on every step.
- Continue until the authorized work can be implemented and checked without silently inventing consequential requirements. Settle uncertainties affecting correctness, scope, architecture, or acceptance with the user before dependent edits. Handle routine implementation details using repository conventions and judgment. Defer unrelated questions explicitly rather than expanding the card or interviewing indefinitely.

Briefly state the resulting scope, essential decisions, and any agreed deferrals before starting. Reuse existing execution authority; do not add a ceremonial approval when the user already authorized the now-defined work. If later evidence exposes a material gap, resume targeted investigation and questions before the affected implementation. An autonomous execution grant does not supply missing product decisions.

## When development without a plan is requested

Honor an explicit request such as “develop without a plan” or “skip planning.” Run the analysis and interview above in the current mode, but do not force native plan mode, create a development plan, or invoke the planning skill merely to satisfy the default workflow. If an existing plan is set aside, preserve its history without pretending it remains synchronized. Higher-priority host mode restrictions still apply.

In this branch, plan creation, plan approval, full plan snapshots, and displayed-plan synchronization gates below do not apply. Keep only a concise conversational record of agreed scope, decisions, blockers, verification, and current execution authority; do not recreate a full plan under another name. Identify the next bounded increment and its completion evidence before editing. Retain the normal per-increment review boundary unless the user explicitly grants broader execution authority; “without a plan” alone does not waive review or authorize unrelated work. Continue to maintain card status, report actual checks, and preserve commit and push authorization boundaries. In teacher mode, retain conceptual navigation and the user's driver role without requiring a learning-plan artifact.

## Obtain an interactive development plan

If no plan exists, use the available `story-development-plan` skill for initial planning before implementation. If an existing plan needs clarification or revision, update it in the current mode, using that skill’s planning guidance when helpful without triggering its initial-plan mode requirement. Pass the story and retrieved context. Invoke it through the host or locate and read its installed instructions; this is a transition in the same conversation, not a new chat or subagent. If it is unavailable, explain the missing dependency and do not claim to have used it.

Planning must remain scoped to the single story and include critical questions about unresolved behavior, design choices, and validation. Keep native plan mode active during initial plan creation; existing-plan revisions may take place in the current execution mode. A physical document is optional; do not require a Notion page or repository file to begin.

Use the planning skill's development-plan format. Each step has one small outcome the user can review quickly, a concise description of the relevant implementation choices, and a focused check with its expected result. Use numbered headings with a short name and `todo`, `doing`, or `done`, without a progress table. When resuming an older plan, bring the headings into this format and split remaining steps that bundle independently reviewable outcomes. Preserve valid work, evidence, and past approvals. Reconcile execution authority as described below before starting a changed step.

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

1. Identify the step's authorized outcome, implementation decisions, prerequisites, and focused verification. Resolve material gaps through the critical interview before dependent edits. If the step still bundles work the user can review independently, revise the plan and reconcile authorization before editing. Mark the authorized step `doing` when a plan is in use.
2. Implement only the work needed for that increment. Necessary changes within the agreed boundary are part of the step; unrelated refactors, modernization, or later-step work are not.
3. Follow applicable repository and technology documentation and skills for actual coding. Prefer established patterns, clear names, cohesive functions or modules, straightforward control flow, and the simplest adequate design. Avoid speculative abstractions and unnecessary dependencies.
4. Write as few comments as necessary. Use comments for non-obvious constraints, invariants, or reasons that code cannot express clearly; avoid narrating obvious operations. Preserve existing comments unless changing them is required by the work or requested, and keep required documentation and public API conventions.
5. Verify the step using its agreed evidence. Add meaningful tests when they prove behavior or prevent a relevant regression, and run appropriate existing checks. Do not add tests merely to mirror the implementation or satisfy a quota. If verification requires user acceptance, present the behavior and the precise review needed.
6. Inspect the relevant diff and check for accidental changes. Repair failures within the step's scope; if blocked, record the obstacle and ask for the decision or access needed. Do not advance with unmet completion criteria or claim an unavailable check passed.
7. Update the step description with the actual changes and verification. Keep it `doing` with review pending, then mark it `done` once the criteria are met and the user approves, or an applicable grant waives review. Record a waiver as such and update the next action.

## Keep the user able to review the code

At each increment, report concisely:

- The outcome and AC or other completion targets addressed.
- The important code changes, with useful file or diff references and the rationale for meaningful choices.
- What was verified, actual results, and any limitations or remaining acceptance check.
- The next step's objective and the current approval boundary.

Show enough concrete evidence for the user to understand and challenge the code without dumping entire files or hiding meaningful trade-offs. Under the default workflow, present the complete updated plan and ask whether to approve this increment and proceed with the named next step. Do not begin it while waiting. Under a valid grant, notify progress and continue only through its remaining coverage.

When the user requests changes during review, keep work on the current step, update the plan, and reverify affected criteria before presenting it again. User approval does not override objective completion criteria; record any explicitly agreed change to those criteria as a plan revision.

## Create focused Gitmoji commits when requested

Commit only when the user requests it or has explicitly authorized committing within the current scope. Approval of an implementation step alone is not commit authority, and a request to commit does not itself authorize pushing or rewriting existing history.

Before committing, inspect the working tree, staged changes, applicable repository instructions, and relevant commit conventions. Group the authorized changes into small, conceptually coherent commits: each commit should have one clear purpose that a reviewer can understand and, where practical, revert independently. Separate unrelated features, fixes, refactors, or housekeeping. Keep necessary implementation, directly related tests, and required documentation together when separating them would leave an incomplete or broken change. Do not impose a fixed number of files, lines, or commits, or create artificial one-file commits merely to make them small. A development step can require several commits, and a small coherent change can require only one.

Use the [Gitmoji specification](https://gitmoji.dev/specification) for each commit subject: `<intention> [scope?][:?] <message>`. Choose one appropriate emoji from the [official Gitmoji list](https://gitmoji.dev/) for the commit's actual purpose. Use the Unicode emoji by default, or its official `:shortcode:` when required by the repository or user. Add a scope only when useful or required. Write a concise, specific description of what changed in the repository's required language; add a body only when the reason, trade-off, or compatibility impact needs explanation. For example, `🐛 Fix expired-session redirect` or `📝 Clarify local setup instructions`. Do not replace the requested Gitmoji format with an unrelated convention or install a CLI or hook merely to format a message.

Stage only the files or hunks belonging to the current logical change and the authorized scope, then inspect the staged diff before each commit. Preserve unrelated user changes and pre-existing staged work; do not sweep them into a commit, discard them, or silently unstage them to simplify splitting. If mixed changes cannot be separated reliably, explain the concrete ambiguity and resolve it before committing. Validate each commit's relevant behavior proportionately, run required repository checks, and do not bypass hooks to force a commit through.

After committing, verify the resulting commit contents and working-tree state. Report the commit hashes and their distinct purposes, together with any relevant uncommitted work or failed checks. Update the resumable plan with the commits that carry the implementation. Do not amend, squash, or rebase existing commits merely to retrofit this granularity without authorization.

## Manage the source card status

When the story, task, or spike has a source tracker card, maintaining its status is part of this workflow and does not require separate permission at each transition. Honor an explicit request to leave the tracker unchanged. This authority covers the source card's status only, not unrelated cards or other properties.

Read the card's current status, the destination's available status options, and established workflow conventions before writing. Map the lifecycle below to existing English values; the example labels are meanings to match, not values to create. Do not create or rename status options or shared properties. If the mapping is ambiguous or labels are non-English, resolve it with the user before the affected write. For pasted stories without a tracker card, keep status in the plan and do not create a card merely to track it.

| Lifecycle event | Source card status |
| --- | --- |
| Context retrieval or planning only | Preserve the current status. |
| First authorized implementation starts, or work resumes after a blocker or requested changes | Use the existing active-work status, such as `In Progress`. |
| All story work and available checks are ready, but final user review or acceptance remains | Use the existing review status, such as `In Review`; if none exists, retain the active-work status and record pending review in the plan. |
| A concrete obstacle prevents further story work | Use the existing blocked status if available; otherwise retain the active status and record the blocker in the plan. |
| All completion targets, required checks, and required final approval are satisfied | Use the existing completed status, such as `Done`. An explicit grant may waive review only within its recorded scope. |

Track the card as a whole: an individual step entering review or completing does not put an unfinished story in review or mark it done. Routine approval gates, session boundaries, and pauses are not blockers. Never mark the card done while required work, checks, or final acceptance remain pending.

Apply each transition at the corresponding checkpoint, skip writes when the card already has the correct status, and verify the saved value through the connector response or a read-back. On resumption, reconcile the live status with the plan and actual work; resolve conflicting external changes before overwriting them. If tracker access or a write fails, report the unsaved transition and retain it in the resume state without claiming synchronization. Continue otherwise authorized work when that failure does not block implementation.

## Adapt the plan during implementation

Maintain the working plan as user feedback and new evidence arrive, and try to persist revisions to the displayed plan in the current mode. Use the end-of-step fallback if that update is unavailable or unsuccessful. Before affected implementation, update decisions, dependencies, step boundaries, coverage, and verification requirements. Explain material revisions and resolve them with the user; do not silently expand the plan under an old approval.

Keep stable step IDs. For a split or replacement, assign new IDs where needed and record the relationship to the previous IDs in the resume state. Invalidate stale evidence when changes affect previously verified work. Retain the distinction between proposed choices and accepted decisions.

If the plan is split, merged, or materially changed, reconcile any bounded grant against the new step IDs with the user rather than extending its coverage automatically. Routine evidence or status updates do not require reapproving the whole plan. If discussion leaves the story's scope, flag it and ask whether to revise scope or park the topic; return to the original boundary when a change is declined.

## Preserve resumability and finish accurately

Keep the development plan separate from the source card. Maintain implementation details, redirects, decisions, checks, approvals, and resume snapshots in the conversation or an explicitly requested separate plan document. Never copy or synchronize that working record into the card, including at skill transitions or review checkpoints.

For authorized tracker updates, keep property names, card types, and status options in English. Reuse existing English status values for every transition; if the schema uses non-English labels, resolve the schema change with the user before writing rather than renaming shared fields automatically.

When tracker updates are authorized, keep story/task edits limited to necessary agreed requirement corrections, existing checklist items, and relevant properties. Preserve their brief description and AC or to-do structure. For a completed spike, save only one concise `Outcome` section summarizing the analysis result; if its deliverable is other cards, include only links to the cards actually created under that heading. Replace obsolete investigation content rather than appending a running report. Keep card headings `Description`, `Outcome`, `Todos`, and `Acceptance criteria` in English; write their content in the project's language and do not create output cards without authorization.

Keep the plan synchronized after meaningful changes, check results, decisions, and approvals, including while executing an authorized batch. Use equivalent fields to the existing plan; do not replace a richer resumable plan with a native checklist that drops context.

If the development plan is already displayed in a side panel, canvas, or connected document, update that same artifact in place through the host's supported editing tool at every plan checkpoint, including during execution outside plan mode. Read the current artifact before editing, preserve user edits, and verify the saved content or returned revision. Updating chat text or a separate progress checklist alone does not establish that the displayed plan was updated. Retain the artifact's identity and latest verified revision in the resume state when available, and pass them across skill transitions; do not create a replacement merely because the mode changed.

Try to persist necessary plan changes alongside development, after meaningful implementation changes, evidence, decisions, or approvals, rather than postponing all updates until the step ends. Discover the supported mechanism for the actual plan surface: a native plan-mode document, a progress checklist, and an editable file or canvas are different objects. Use only capabilities actually exposed by the host, and verify that the intended plan was updated. A missing capability is a failed synchronization attempt, not a reason to invent calls or repeatedly retry an unavailable mechanism. Material revisions still require the applicable scope decisions and execution approvals above.

If the displayed plan cannot be updated or its saved state cannot be verified, keep the complete working plan current in the conversation and record the pending changes and reason in the resume state. Finish the currently authorized step and its checks when safe; unresolved requirements or execution authority may still require an earlier stop. At the end of that step, explicitly state that the displayed plan needs updating, summarize the pending changes, and ask the user to activate native plan mode so the revised plan can be published. Make this request even under a multi-step or story-wide execution grant, and even at the final step. Wait for the host to confirm plan mode before proceeding to another implementation step; silence is not a mode switch. If work stops before the step ends, include the same notice and request in that checkpoint.

Once the host confirms plan mode, reconcile and publish the full revised plan through the host's supported plan-output mechanism. For a native plan-mode document, use the host-required proposed-plan format rather than treating it as an editable canvas or claiming to mutate the old document. Verify the resulting plan when the host exposes confirmation; otherwise report the verification limitation. Clear pending synchronization only when established by that evidence. Return to execution through supported host controls, explaining any required user action, and retain the remaining execution grant without requesting it again. If native plan mode is unavailable, explain that this fallback cannot run and provide the current copyable plan without claiming the side view was updated.

Update each step's status in its numbered heading and keep every step visible in full plan snapshots. Note pending review or blockers in the description or resume state, using the three heading statuses throughout. Use the user's or project's language for the plan prose.

At every approval gate, pause, blocker, batch boundary, or session end, provide the full current plan in a copyable form. Include the brief description, story/AC snapshot, repository identity, branch and observed commit when available, relevant paths and uncommitted work, all steps and statuses, evidence and reviews, decisions, blockers, active/next step, remaining grant, and exact next action. Do not require a separate stored document or permission to create one merely to maintain this conversational plan.

When resuming in another chat, first compare that snapshot with the actual checkout and current story. A pasted plan does not transfer source changes; recover missing code or ask for it rather than recreating work from an unsupported status.

When all increments meet their criteria, check overall story coverage and relevant integration behavior. Distinguish technically complete work from pending user review. Without a broader grant, the final increment also requires approval before declaring the story complete. Update the source card status under the lifecycle rules above, report remaining gaps honestly, and leave the final plan ready to copy. Do not infer authorization to commit, push, deploy, or make unrelated tracker edits from completion of coding alone.

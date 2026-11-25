# Resumable development plan

The plan is both the agreed implementation sequence and the current handoff state. Make it self-contained enough to review and resume in another chat. Use the user's or project's required language for the prose and the three status tokens below for step headings.

## Required content

- **Brief description:** the problem and intended result for this story.
- **Story and scope:** source reference when available, a compact snapshot of the relevant AC or completion targets with stable labels, constraints, and exclusions. Include enough context to resume even if the source cannot immediately be fetched.
- **Repository context:** repository or checkout identity, branch and commit when available, relevant paths, documentation or skill references, and the actual state of existing or uncommitted work.
- **Steps:** one heading per step with its stable number, short name, and status. Follow it with concise prose covering one small outcome, the implementation decisions needed to review it, and a focused verification with an expected result. Record actual evidence and review disposition there when available. Mention a prerequisite or link to a completion target only when it clarifies the step.
- **Current state:** active or next step, plan revision, unresolved questions or blockers, accepted decisions, exact next action, and execution authority.

Use the format below without a progress table or a second list of step titles. Keep steps in dependency order. When revising an older plan, fold any separate progress list into the step headings and retain the existing decisions, evidence, and approvals. Keep the surrounding sections compact and omit fields with no information useful for review or resumption.

```markdown
# Development plan: [Story title]

## Description
[Brief problem and intended result.]

## Story and scope
- Source: [Card/issue URL or supplied story text reference.]
- Completion targets: [AC-1: ...; AC-2: ...; or task/spike targets.]
- Constraints and exclusions: [...]

## Repository context
- Repository / checkout: [...]
- Branch / observed commit: [... or unavailable.]
- Relevant code and guidance: [...]
- Working tree / existing work: [...]

## Steps

### 1. [Short step name] — todo

[Describe the outcome and the concrete implementation choices, naming the affected component, contract, or documentation section when helpful.]

[State how to verify this change and what should happen. Add the actual check result and review disposition when available.]

[Repeat the heading and concise description for each additional step.]

## Resume state
- Revision: [Plan revision.]
- Current / next step: [...]
- Decisions: [Accepted choices and essential rationale.]
- Open questions / blockers: [... or none.]
- Execution authority: [Default per-step review or exact explicit grant.]
- Grant remaining: [Authorized step IDs or none.]
- Last approval / review: [What the user actually approved, or none.]
- Next action: [The precise authorized action or approval question.]
- Displayed plan: [Existing artifact reference and latest verified revision, when available; otherwise unavailable or not applicable.]
- Pending plan synchronization: [Unsaved changes, failure or unavailable capability, and required mode-switch action; or none.]
```

Do not leave template placeholders in a delivered plan. Use “unknown,” “not run,” or “not applicable” where accurate, and ask when an unknown blocks the next action. Add fields only when they help implementation or resumption.

Before presenting the plan, check that each step can be reviewed quickly at its place in the sequence and that the full sequence covers the card. A description should let the reviewer anticipate what will change and how to check it. Expand it only where a consequential choice or integration would otherwise be unclear.

## State and approval

- `todo` means work has yet to start.
- `doing` starts before the authorized edits and continues through pending checks or review.
- `done` means the completion criteria are met and the user approved the step or an explicit grant waived that review.

Record pending review, requested changes, waived review, and concrete blockers in the description or resume state when relevant. A blocker keeps the step at `todo` or `doing` according to whether it has started. When an agreed revision replaces a step, record its old identifier and replacements in the resume state so recorded approvals remain traceable. Passing checks do not grant approval, and waived review does not satisfy unmet completion criteria.

## Keep the plan current

These updates apply to the working plan in the conversation or an explicitly requested separate plan document, never to the source backlog card. Do not append plan snapshots or a development history to that card.

After a decision, meaningful implementation change, check result, or approval, update the affected descriptions, heading statuses, and resume state. Keep all current steps visible, including those already done. Preserve stable step identifiers and previous approvals when revising the sequence. When changing a completed step's obligations, invalidate affected completion or evidence and explain what must be reverified.

When an existing side view or connected document displays the plan, persist those updates to the same artifact using the host's supported editing tool and verify the saved content or revision. Preserve its identity across planning and execution. Try to synchronize necessary revisions alongside development in the current mode; applicable scope and execution approvals still apply. A chat snapshot or separate checklist is not evidence that the side view changed. Record any failed or unavailable synchronization and pending changes in the resume state. At the end of the current authorized step, or an earlier stopping checkpoint, explicitly say that the displayed plan needs updating and ask the user to activate native plan mode. This fallback also applies under broader execution grants. Wait for host confirmation, publish the full revised plan using the supported plan-output mechanism, and retain the remaining execution authority when returning to implementation. Do not claim the displayed copy is current without verification.

At every approval gate, pause, blocker, session end, or requested handoff, provide the complete current plan in a copyable form. A short progress message or a native list of step titles alone is not sufficient for resumption. Under an authorized multi-step batch, keep the working plan current after every step and present the full snapshot at the batch boundary rather than demanding intermediate approval.

The plan records code state; it does not transport code. For resumption elsewhere, identify the checkout, commits, and uncommitted work that must be available. Do not claim that pasting the plan reconstructs missing changes or commit work merely to make the plan portable.

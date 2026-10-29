# Resumable development plan

The plan is both the agreed implementation sequence and the current handoff state. Keep it concise and self-contained enough to paste into another chat without relying on messages such as “as discussed above.” Use the user's or project's required language.

## Required content

- **Brief description:** the problem and intended result for this story.
- **Story and scope:** source reference when available, a compact snapshot of the relevant AC or completion targets with stable labels, constraints, and exclusions. Include enough context to resume even if the source cannot immediately be fetched.
- **Repository context:** repository or checkout identity, branch and commit when available, relevant paths, documentation or skill references, and the actual state of existing or uncommitted work.
- **Incremental steps:** a progress table covering every step, followed by details with stable IDs, outcome, coverage, implementation boundary, completion criteria, validation, explicit current status, and review evidence.
- **Current state:** active or next step, plan revision, unresolved questions or blockers, accepted decisions, exact next action, and execution authority.

Use this structure as a compact default. Preserve a supplied plan's equivalent structure instead of reformatting it unnecessarily:

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

## Incremental steps

| Step | Outcome | Status |
| --- | --- | --- |
| S1 | [Outcome] | planned |

[Include every step in this table, including completed and unstarted steps.]

### S1 — [Outcome]
- Status: planned
- Covers: [Completion targets or necessary enabling work.]
- Change boundary: [Behavior, components, or relevant paths.]
- Depends on: [Step IDs or none.]
- Done when: [Specific, determinable criteria.]
- Verification: [Test/check or explicit user acceptance and what to review.]
- Evidence: [Not run yet, or actual result and remaining gaps.]
- Review: pending

[Additional steps with the same fields as needed.]

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

## State and approval

| Step status | Meaning |
| --- | --- |
| `planned` | To do: not started. |
| `in_progress` | Work started; completion criteria are not yet met. |
| `awaiting_review` | Implementation and available checks are ready for the user's review; any required human acceptance is still pending. |
| `completed` | Done: completion criteria met and the user approved the increment, or an explicit execution grant waived the intermediate review. |
| `blocked` | A concrete obstacle prevents completion. Record what is needed. |
| `superseded` | An agreed plan change replaced this step. Preserve its identifier and disposition. |

Record review separately: pending, user-approved, changes-requested, or waived under a specific grant. Never label an automatically continued step “user-approved.” A passing test or an elapsed wait is not user approval. A grant may waive intermediate review; it does not make failing checks pass.

Every step must have exactly one current status, shown both in the progress table and its details. Initialize new, unstarted steps as `planned`, mark the authorized step `in_progress` before implementation, and update it as verification and review change its state. A blocked step or one awaiting review is not `completed`. Render labels in the user's or project's required language while preserving these meanings.

## Keep the plan current

These updates apply to the working plan in the conversation or an explicitly requested separate plan document, never to the source backlog card. Do not append plan snapshots or a development history to that card.

After a decision, meaningful implementation change, check result, or approval, update affected plan fields, the progress table, and the resume state together. Keep the status of every step visible, including work still to do and work already done; do not replace the complete progress table with only the active step. Preserve stable step IDs; do not silently renumber pending work or erase previous approvals. When changing a completed step's obligations, invalidate affected completion or evidence and explain what must be reverified.

When an existing side view or connected document displays the plan, persist those updates to the same artifact using the host's supported editing tool and verify the saved content or revision. Preserve its identity across planning and execution. Try to synchronize necessary revisions alongside development in the current mode; applicable scope and execution approvals still apply. A chat snapshot or separate checklist is not evidence that the side view changed. Record any failed or unavailable synchronization and pending changes in the resume state. At the end of the current authorized step, or an earlier stopping checkpoint, explicitly say that the displayed plan needs updating and ask the user to activate native plan mode. This fallback also applies under broader execution grants. Wait for host confirmation, publish the full revised plan using the supported plan-output mechanism, and retain the remaining execution authority when returning to implementation. Do not claim the displayed copy is current without verification.

At every approval gate, pause, blocker, session end, or requested handoff, provide the complete current plan in a copyable form. A short progress message or a native list of step titles alone is not sufficient for resumption. Under an authorized multi-step batch, keep the working plan current after every step and present the full snapshot at the batch boundary rather than demanding intermediate approval.

The plan records code state; it does not transport code. For resumption elsewhere, identify the checkout, commits, and uncommitted work that must be available. Do not claim that pasting the plan reconstructs missing changes or commit work merely to make the plan portable.

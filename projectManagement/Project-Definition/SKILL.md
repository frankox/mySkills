---
name: project-definition
description: Refine a project idea through a critical, adaptive interview before building it. Establish scope and analysis depth first, ask before changing either, and offer a handoff to project-documentation when the agreed definition is sufficient.
---

# Project-Definition

Help the user turn an idea into a sufficiently clear project definition for their current purpose. Investigate assumptions and trade-offs through sustained questioning. Do not implement the project or write project documentation in this phase.

## Agree on the session before substantive questions

1. **Depth first.** Ask the user to choose an analysis level from the table below, explaining the practical difference. If they already explicitly specified a level, confirm what it means for this session rather than silently selecting one. Wait for their answer before project-detail questions.
2. **Precise scope.** Use an already stated, precise scope; otherwise ask what outcome this conversation must achieve and which part of the idea is included. A topic such as “my app” is not yet a precise scope. Clarify exclusions when the boundary is unclear.
3. State a short session contract: objective, in-scope topics, exclusions, chosen depth, and the condition for a sufficient definition. Resolve ambiguity before starting the interview. Do not expand an already clear scope while restating it.

| Depth | Purpose and sufficient definition | Stay away from |
| --- | --- | --- |
| Explore | Clarify the idea, intended audience, problem, possible value, and the main hypotheses or alternatives relevant to the session objective. Uncertainty may remain explicit. | Detailed specifications, exhaustive edge cases, or architecture choices that do not decide the idea's viability. |
| Define | Agree on the problem, intended outcomes, main user flows or activities, minimum useful scope, exclusions, success criteria, constraints, and important risks relevant to the objective. | Implementation detail that does not affect these decisions. |
| Detail | Resolve the scoped behaviors, relevant edge cases, dependencies, interfaces, data or operational constraints, and validation criteria needed to prepare for the next delivery step. | Unrelated systems, exhaustive design outside the agreed boundary, or starting implementation. |

These are depth profiles, not mandatory document sections or a demand to discuss every topic. Customize the completion condition to the actual scope. Exploration is a valid outcome; do not treat it as unfinished detailed planning.

## Interview to resolve decisions

- Ask many useful questions over successive exchanges, not a long questionnaire up front. Usually ask one focused question; group up to three only when their answers are independent and easy to give together. Wait for answers before dependent follow-ups.
- Choose the next question by its effect on the agreed outcome. Resolve decisions that constrain later choices before asking for those choices. Follow relevant threads until resolved, explicitly deferred, or excluded.
- Be constructive and skeptical: challenge unsupported assumptions, expose contradictions, compare credible alternatives, and ask for concrete examples at the chosen depth. Do not argue for its own sake or steer every idea toward a predetermined solution.
- Offer a tentative recommendation or a few meaningful options when this helps the user decide. Distinguish your proposal from the user's decision; unanswered suggestions are not agreement.
- Read relevant available project context to resolve factual questions instead of asking the user to repeat it. Keep investigation proportionate to the scope and depth; ask the user for preferences and decisions that sources cannot establish.
- Maintain a compact conversational record of the session contract, confirmed decisions and essential rationale, assumptions, unresolved questions, and parked topics. Update changed decisions instead of accumulating contradictory summaries. Do not save session files or create external artifacts before the documentation handoff is accepted.
- Do not repeat answered questions unless new evidence creates a conflict. If an answer is unknown, distinguish a blocker from uncertainty that can remain at this depth; agree on deferral where appropriate.

## Enforce scope and depth throughout

Before each new line of questioning, compare it with the session contract.

**Scope drift:** If a user answer or proposed question moves into another problem, audience, feature set, or outcome outside the boundary, name the specific change. Ask whether to redefine the scope or park that topic and return to the current scope. Do not pursue the new branch while that choice is pending. If the user declines a scope change, return the conversation and next question to the original boundary.

**Depth drift:** If the conversation begins requiring more detail than agreed, state what additional analysis would be involved. Ask whether to increase the depth or keep the original level and defer that detail. Increased depth does not authorize broader scope. If the user wants a lighter level, make that change explicit and reconfirm what now counts as sufficient.

When both boundaries change, resolve scope and depth explicitly; approval of one is not approval of the other. After an accepted change, restate only the changed contract fields and reassess the remaining questions. Do not infer approval from silence or from the user merely mentioning an adjacent topic.

## Recognize when the idea is sufficiently defined

Stop probing when the agreed outcome can be explained coherently at the chosen depth, the relevant decisions are settled, and remaining uncertainty is explicitly acceptable or deferred. Do not require every conceivable question to be answered or continue merely to reach a question count.

Give a concise checkpoint covering:

- The resulting definition and its intended outcome.
- The agreed scope, depth, and major decisions.
- Any remaining assumptions, blockers, deferred questions, or excluded topics.

If the completion condition is not met, say what is still missing and ask the next useful in-scope question. A user may stop early; preserve the partial state without claiming the definition is complete.

When sufficient, explicitly ask whether to begin documenting the idea. Wait for the answer. If the user declines, close with the concise definition or continue only the refinement they request within the agreed boundaries.

## Hand off to Project-Documentation

After the user accepts documentation, activate the available `project-documentation` skill and pass the compact state below. Use the host's skill mechanism, or locate and read that installed skill's instructions if no invocation mechanism exists. This is a workflow transition in the current conversation, not an instruction to create another chat, message another agent, or start implementation.

Pass:

- Session objective, included and excluded scope, depth, and completion condition.
- Current project definition and intended outcomes.
- Confirmed decisions with essential rationale; distinguish proposals and assumptions.
- Unresolved or deferred questions and parked topics.
- Relevant source links or file paths and any already supplied destination or language preference.
- The user's consent to start documentation.

The receiving skill must first resolve the documentation destination: **Notion or an existing repository**. Do not choose a destination or create documents on its behalf. If the skill is unavailable, preserve the handoff state and explain that limitation; do not claim a handoff occurred.

## Method reference

Inspired by [grill-me](https://github.com/mattpocock/skills/blob/main/skills/productivity/grill-me/SKILL.md) and its [grilling workflow](https://github.com/mattpocock/skills/blob/main/skills/productivity/grilling/SKILL.md). These links explain the inspiration; this skill is self-contained and does not require installing those skills.

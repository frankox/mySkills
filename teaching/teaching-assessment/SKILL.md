---
name: teaching-assessment
description: Plan a school assessment with the teacher using Notion lessons and native plan mode, ask whether to use Onlitest, and create the assessment page in Notion when implementing the agreed plan. Include progressive practical tasks, a common route to 6/10, and a scoring rubric.
---

# Teaching Assessment

Prepare one common assessment with clear evidence of mastery at each grade. Work with the teacher on its design before producing the final assessment.

## Resolve inputs and retrieve lessons first

1. Recover the **subject** and **topic or topics** from the request and conversation. Ask for either missing input, together when both are missing. Do not infer a subject from an ambiguous topic or ask again for supplied information.
2. Load `teaching-context` through the host's skill mechanism or locate and read its installed `SKILL.md`. This is a required shared dependency. If unavailable, report the missing dependency and resolve it before claiming to follow this workflow. Do not duplicate or guess its School binding.
3. Follow that skill to resolve School, search relevant lessons, read their content, and identify taught topics and practiced tasks. If class or year is needed to select between materially different lessons, ask at this point.
4. If no relevant lessons are found, explicitly notify the teacher and request the topics, syllabus, notes, or lesson text directly. Reuse sufficient material already provided. Distinguish missing lessons from failed access. For partial coverage, resolve the missing material or its exclusion before designing affected items.

Do not ask assessment-design questions or draft the assessment before this source step is complete. A resolved fallback consists of teacher-supplied material sufficient to define the taught scope; it does not require creating lessons in Notion.

## Enter native plan mode autonomously

After retrieving the relevant lessons or resolving the teacher-supplied fallback, activate the host's native plan mode through its supported mechanism, without asking permission when the agent can switch. If already active, continue there.

If higher-priority instructions prevent switching or no agent-controlled switch is exposed, explain the limitation briefly and ask the teacher to activate native plan mode. Wait for host confirmation before preparing or revising the assessment plan. Do not claim that a planning tool or a planning-only conversation changed the host's mode. If native plan mode is unavailable, explain that this workflow cannot continue as requested in that host.

Remain in native plan mode while collaboratively designing the assessment. Once the design is agreed and the teacher moves to implementation, including leaving plan mode to execute that agreed plan, proceed to create the assessment page in Notion as described below. This implementation step includes the Notion write; do not ask for separate permission to save. Use the supported host transition when needed. Honor existing authorization; do not add approval gates for individual questions or exercises. A mode change with unresolved design decisions does not settle those decisions; resolve only what blocks implementation.

## Design the assessment together

Summarize the retrieved coverage and propose a concrete design the teacher can adjust. Ask focused questions, normally one to three at a time, only for unresolved decisions that affect the result: class or level, duration, practical environment, permitted tools, required access arrangements, or output format. Reuse known constraints and label proposed defaults.

Explicitly ask **whether to use Onlitest**, unless the teacher has already answered. Do not assume either choice. Record the answer in the plan. If yes, propose a populated, copy-ready template for the Onlitest chatbot using [the Onlitest handoff template](references/onlitest-handoff.md). Review it together with the assessment design. If no, prepare the assessment without an Onlitest handoff.

During planning, locate the actual **Verifiche** section within Scuola through `teaching-context`. Inspect its destination page or collection, current schema, templates, view filters, and relevant existing assessment conventions. Prepare a mapping from the agreed assessment metadata to the destination's writable properties. Resolve missing required values and ambiguous relations during planning so implementation can create a correctly filed page. This is read-only preparation; do not create a placeholder assessment while still in plan mode.

Keep a current plan in the conversation containing the taught scope and sources, learning objectives, the ordered item outline, difficulty progression, estimated time, scoring and grade conversion, Onlitest choice and handoff when selected, the resolved Notion destination and proposed property values, and open decisions. For each proposed item, state the skill being assessed, expected evidence, and available points. Revise the plan as the teacher responds rather than generating the entire test immediately. A separate saved plan is optional.

## One common assessment and common standards

- Design a common assessment that does not need a separate simplified version. Use clear language, readable instructions, explicit deliverables, and manageable steps without revealing the answers.
- Give a student who has studied, including a student with difficulties, a realistic and accessible route to **6/10** through preliminary theory and **one very simple practical exercise**. This is a design target, not a guarantee of an individual's result.
- Preserve applicable arrangements already supplied by the teacher, including those in a PDP. Ask only for functional requirements relevant to the task. The common assessment does not cancel agreed support, tools, or timing arrangements.
- Use the same learning objectives, observable achievement descriptors, and grade meaning for all students taking this assessment. Do not award the same grade for materially different levels of demonstrated mastery or lower a threshold merely because a student has a PDP. If the teacher identifies different objectives, resolve how results will be interpreted rather than asserting equivalence.
- Make higher grades substantially harder to earn through deeper reasoning, independent application, integration, or transfer of taught knowledge. Do not manufacture difficulty through ambiguous wording, excessive workload, or untaught prerequisites.

## Structure, progression, and points

1. Begin with a short block of theoretical questions, progressing from basic recall or understanding toward explanation. Keep this preliminary block smaller than the practical component by both expected working time and points.
2. Follow with one very simple practical exercise directly based on practiced skills. Together with the theoretical block, its full credit must reach the **6/10 threshold** without requiring any harder item. Theory alone must remain below that threshold.
3. Add increasingly demanding practical exercises. Each successive question or exercise must require a clear increase in cognitive demand, autonomy, or integration. Check the progression across section boundaries as well as within each section.
4. Keep later exercises independently attemptable where possible. If one builds on an earlier result, supply a neutral starting value or award follow-through credit so an early error does not erase unrelated evidence of mastery.
5. Prefer a total score that is a **multiple of 10**, such as 50 or 100. This is a preference, not a reason to distort useful weights. Explain a proposed exception and settle it with the teacher during planning.
6. State the score-to-grade rule, thresholds, and rounding policy. With proportional conversion, use `grade = 10 * earned_points / total_points`, and allocate exactly `0.60 * total_points` to the theoretical block plus the very simple practical exercise. If the teacher supplies another conversion, use its actual 6/10 threshold and verify the same accessible route.

For example, a 100-point design could assign 20 points to preliminary theory, 40 to the very simple practical exercise, and 40 to progressively harder practical tasks. This leaves 80% of points for practice. Adjust weights and item counts to the taught material and duration while preserving the 6/10 route. Distinguish 7–8 from 9–10 through explicit mastery descriptors; higher marks must require evidence from the harder tasks.

## Mandatory evaluation table

Every assessment must include an evaluation table, including substantive drafts. A planning outline must already show the proposed point allocation. The table must identify each question or exercise, the knowledge or skill assessed, observable full and partial credit criteria, and maximum points. Break a complex exercise into scored criteria where needed and make the total visible.

Include a score-to-grade table or clearly stated conversion alongside the evaluation table, with explicit descriptions of the evidence needed for 6/10 and higher grades. Decide rounding so a score below the intended pass threshold does not silently receive 6 through rounding. Keep descriptors and calculation consistent; do not promise a mastery level the points can award without its required evidence.

Provide the grading criteria with the student-facing assessment. Keep model answers, worked solutions, and detailed correction notes in a clearly separate teacher section or artifact so the student paper does not disclose solutions. Prepare a correction key sufficient to check feasibility and apply partial credit consistently.

## Verify and deliver

Before presenting a substantive draft or final assessment:

- Solve the tasks and check that they are unambiguous, feasible in the allowed environment and time, and supported by the retrieved lessons or teacher-supplied scope.
- Check each increase in difficulty, including the theory-to-practice transition, and make sure the basic practical exercise remains accessible.
- Sum item and criterion points; verify the stated total, conversion, thresholds, and rounding. Confirm that theory plus the simple exercise earns 6/10 and theory alone cannot.
- Check that practical work dominates both points and estimated time, and that high grades require the intended advanced evidence under the actual partial credit rules.
- Ensure the evaluation table is present, common grade descriptors remain consistent, and solutions are separate from the student paper.

Present the assessment in the user's or destination project's language, with subject, topics, time, permitted tools, numbered tasks, point values, and the evaluation table. Identify source lessons and any teacher-supplied coverage in the teacher notes. Use an available document or PDF skill if that format is requested. If Onlitest is selected, check that its populated handoff reproduces the agreed assessment, points, answers, and grading rules without contradicting the Notion version.

## Implement by creating the Notion assessment page

Implementation means creating the prepared assessment in **Verifiche**, within the confirmed Scuola area. Producing only a chat response or an Onlitest prompt does not complete implementation. This applies whether or not Onlitest is selected. Do not create or publish an assessment in Onlitest itself unless separately requested; the requested Onlitest deliverable is the chatbot handoff.

1. Use the agreed plan and resolved destination. Recheck the destination schema if needed before writing. If Verifiche is a linked or filtered collection, use its actual underlying data source and populate the properties needed for the assessment to appear in that section. If it is a normal page, create the assessment beneath it and follow its existing organization. Do not save at the wiki root merely because the assessment section is inaccessible.
2. Fill every applicable writable property supported by the actual schema, using the agreed information and existing conventions. Depending on that schema, this may include title, subject, topics, class, duration, assessment date, lifecycle status, total points, lesson relations, and Onlitest choice or link. These are mapping examples, not assumed field names. Use exact existing property names, option values, and valid relation targets; distinguish assessment dates from preparation dates. Do not invent a schedule, an Onlitest URL, a completed or administered status, or missing required information. Leave legitimately unknown optional properties unset and identify them in the delivery note. Leave formulas, rollups, and system-managed properties to Notion.
3. Use the destination's supported parent type and page template. The wiki root's page-parent rule does not imply that a separate assessment collection accepts that same parent type. If required properties cannot be set with the available connector, report that limitation rather than claiming the page is fully populated or replacing actual properties with body text. Do not alter the schema to bypass a missing field or option without a request covering that change.
4. Create one page with the final assessment, evaluation table, grade conversion, source references, and separate teacher correction notes. When Onlitest is selected, also include the populated chatbot handoff in the teacher section. Follow the destination's access conventions so solutions and chatbot answer keys are not exposed in a student-facing page.
5. Fetch the created page and verify its parent or collection membership, all supplied property values, lesson relations, complete content, scoring tables, and the Onlitest handoff when selected. Confirm that the page satisfies any relevant Verifiche view filters. If a write returns an uncertain result, inspect the destination before retrying to avoid duplicates. When resuming this implementation, reuse its already-created page rather than creating it again.
6. Return the verified Notion page link and, when selected, the copy-ready Onlitest handoff. State any unfilled optional metadata or failed verification accurately. If access or a required value blocks creation, preserve the prepared assessment, explain the exact blocker, and request only the missing input or access; do not report implementation as complete.

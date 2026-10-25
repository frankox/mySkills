---
name: project-documentation
description: Continue a project-definition interview while maintaining concise, accurate documentation in Notion or an existing repository. Recover current context, reuse existing documents and conventions, enforce agreed scope and depth, and route specialized document work to available skills.
---

# Project-Documentation

Continue refining an idea while documenting its current, agreed definition. Preserve the previous conversation's decisions, scope, and depth instead of restarting discovery. Documentation is the deliverable; implementation is a separate task.

## First resolve where to save

Your first interaction must resolve the destination: **Notion or an existing repository?** Do not choose the current working directory by default. If the user already explicitly chose one, acknowledge it and ask only for any missing destination details.

- **Notion:** identify the existing project area and the exact parent page or database. Use an available Notion connector or equivalent integration.
- **Existing repository:** identify the existing checkout or repository and its documentation area. Read it through available repository tools; do not initialize a new repository.

Do not write until the destination is unambiguous and accessible. Ask for missing access or location information rather than silently switching destinations. If the user has not authorized documentation yet, obtain that decision as well.

## Recover context before any write

1. Recover the preceding conversation or handoff: objective, in-scope and excluded topics, analysis depth, completion condition, decisions and rationale, assumptions, open questions, and source references. Ask only for missing or conflicting information. If no usable prior context exists, ask for and agree on depth first, then establish a precise scope and completion condition before substantive interviewing, using the profiles below.
2. Inspect destination instructions and documentation conventions: hierarchy, templates, language, headings, filenames or page titles, metadata, links, and any applicable repository instructions or Notion properties.
3. Search for existing documentation of the same project and concepts, including synonyms and linked parent or index pages. Read the relevant current sources; matching only exact document titles is insufficient. Keep searches targeted rather than loading the entire repository or workspace.
4. Identify the authoritative document for each topic and what actually needs to change. Prefer updating the existing source over creating parallel documentation. If competing sources, unclear ownership, or contradictory decisions prevent a reliable update, ask before writing.
5. Compare prior documentation with the conversation. Explicitly superseded decisions may be updated; unresolved conflicts require a question. Distinguish the existing implementation from the proposed target state. Do not present a conversational preference as an implemented capability or an assumption as a confirmed requirement.
6. Discover available skills for the document types actually needed. Read and use a suitable specialist before writing that type; pass the established context and destination rather than repeating the interview. If no applicable skill exists, write using this workflow and local conventions. Do not install a new skill or invent a specialized workflow just to satisfy this step.

Before writing, read [the documentation guide](references/documentation-guide.md) for destination handling, concise content, and verification.

## Continue the interview without losing boundaries

Use the inherited session contract. If depth must be established, offer:

| Depth | Work toward |
| --- | --- |
| Explore | A clear idea, audience, problem, possible value, and explicit hypotheses or alternatives. |
| Define | Agreed outcomes, main flows, minimum useful scope, exclusions, success criteria, constraints, and relevant risks. |
| Detail | Scoped behaviors, edge cases, dependencies, interfaces, and validation criteria needed for the next delivery step. |

The chosen scope determines which topics matter; the table is not a required document outline.

- Ask focused questions across successive turns, usually one at a time and at most three independent questions together. Resolve prerequisite decisions first. Challenge ambiguity and weak assumptions, and offer clearly labeled options or recommendations when useful.
- Retrieve facts from accessible context rather than re-asking answered questions. Keep proposed choices separate from accepted decisions. Ask about unresolved conflicts; preserve acceptable unknowns explicitly.
- If scope drifts, explain the specific boundary crossing and ask whether to redefine scope or park the topic and return. If the user declines, resume the current scope.
- If depth drifts, explain the extra analysis and ask whether to increase the level or keep the current one. Confirm a requested decrease too. Do not treat a depth increase as permission to widen scope.
- Pause the affected line of questioning and documentation while a boundary decision is pending. Update the session contract only after the user's answer.

Do not restart the entire questionnaire merely because documentation has begun. Ask only what is needed to accurately document the agreed outcome or continue authorized refinement.

## Keep documentation current and economical

Maintain the smallest coherent set of documents that preserves the meaning of the agreed definition. Adapt to the destination's structure and language; English skill instructions do not require English project documents.

After a meaningful decision, correction, or resolved topic, update the affected canonical section or pass the change to its specialist. Write deltas rather than rewriting unrelated content. Do not persist every message or duplicate the transcript. If nothing materially changed, do not write.

Capture only information useful for the objective: the definition, scope and exclusions, relevant outcomes or behaviors, decisions and essential rationale, constraints, and material open questions. Omit irrelevant categories and empty template sections. Do not remove important qualifiers or uncertainty to save tokens.

Keep terms stable, link to existing definitions instead of repeating them, and make confirmed facts, proposed changes, assumptions, and open decisions distinguishable. Prefer compact natural language over cryptic shorthand. A shorter document that changes the meaning is not an improvement.

## Route specialized deliverables

When an available skill covers a requested deliverable, transition that portion of the work to it. Supply the objective, scope, depth, confirmed decisions, unresolved questions, existing document references, exact destination, language, and authorized operation. Resume this workflow for the remaining project documentation.

For example, use `notion-story-creation` for requested Notion backlog cards; it must still resolve the `story`/`task`/`spike` type. Do not turn a project-definition document into backlog cards unless the user requested them. Use other available specialists for PRDs, decision records, or other formats only when applicable. Do not manufacture ADRs or glossaries by default.

A handoff means using the relevant skill in this conversation, not creating another chat or delegating to another agent. If a required specialist cannot be loaded, explain the limitation and keep its portion pending rather than claiming it was used.

## Verify and close

Check the saved result using the guide after each meaningful update. Preserve consistency with the latest agreed decisions and explain failures accurately. If a write has an uncertain outcome, inspect the destination before retrying.

Stop when the agreed definition is documented at the chosen depth, required updates are verified, and remaining questions are explicitly deferred or accepted. Give the document links or paths and a brief statement of material changes and unresolved items. If the user stops earlier, save only supported partial conclusions and mark the work incomplete.

Do not start implementation, create another repository, publish a site, or commit or push repository changes merely because the documentation is complete.

## Method reference

Inspired by [grill-with-docs](https://github.com/mattpocock/skills/blob/main/skills/engineering/grill-with-docs/SKILL.md). The interview and documentation workflow is defined here; upstream skills are not runtime dependencies.

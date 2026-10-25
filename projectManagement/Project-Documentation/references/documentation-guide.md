# Documentation guide

Use this guide after choosing the destination and recovering its current context, before the first write. Reuse it for later updates; repeat targeted reads when a source may have changed.

## Fit the destination

### Existing repository

- Read applicable repository instructions, the documentation entry point, and representative documents relevant to this project. Check the working tree before editing so unrelated user changes are preserved.
- Follow existing directories, document types, naming, heading hierarchy, metadata, language, and link style. Do not impose `docs/`, a PRD template, or a new knowledge structure on an established project.
- Locate the existing canonical section for the topic and edit it in place. Create a new file only for uncovered content that needs a separate retrieval unit; add it to an existing index if that is the repository convention.
- If the repository has no documentation convention, propose the smallest suitable location and outline, then resolve that choice with the user before writing. Do not initialize a new repository.
- Follow existing rules for historical decisions: preserve decision records and mark superseded decisions using the local convention rather than silently rewriting their history.

### Notion

- Fetch the chosen parent or database, relevant linked documents, representative nearby pages, and applicable templates or properties. Confirm the project relation and source of truth where relevant.
- Match the area's page hierarchy, language, headings, blocks, property values, and link conventions. Use native blocks where supported and do not invent database fields or change the schema automatically.
- Update the canonical page or section when it already covers the topic. Create a child page or database entry only for a real documentation gap in the chosen destination.
- If the area has no clear convention, agree on the minimal page placement and structure before creating it. If a create or update response is ambiguous, fetch or search before retrying to avoid duplicates.

## Keep meaning while minimizing tokens

- Write for retrieval and action: short descriptive headings, direct statements, and one authoritative location for each fact. Use lists for parallel items and tables only for useful comparisons or mappings.
- Preserve the problem, intended outcome, boundaries, essential constraints, accepted decisions, material rationale, and consequential unknowns. Include measurable criteria only when established; do not invent numbers to make a definition appear complete.
- Remove conversational filler, repeated summaries, transcript-style Q&A, duplicated context, empty sections, and speculative detail beyond the agreed depth.
- Keep exact domain terms and identifiers. Define an unfamiliar term once when necessary, then reuse it. Do not introduce opaque abbreviations just to reduce token count.
- Separate current behavior from intended changes. Label proposals, assumptions, unresolved decisions, and deferred topics using the destination's conventions. Uncertainty is useful context, not clutter to remove.
- Link to supporting sources or related canonical documents where this aids verification. Avoid copying large source excerpts or embedding an entire previous conversation.
- Split documents only when the content has distinct retrieval or maintenance needs. Avoid both a sprawling master document and many tiny files that require repeated context loading.
- Update settled changes in small batches. Check whether the text already reflects the latest decision before writing; do not add a progress log unless the destination requires one.

If there is no established outline, propose only the sections needed from this compact fallback:

```markdown
# [Project or idea name]

## Purpose
[Problem, intended audience, and intended outcome.]

## Scope
[Included work and explicit exclusions.]

## Definition
[Agreed concept or behaviors, at the chosen depth.]

## Decisions and constraints
[Accepted choices, essential rationale, and relevant constraints.]

## Open questions
[Material assumptions, unresolved decisions, and accepted deferrals.]
```

This is an optional outline, not permission to replace the destination's structure or generate empty sections. Record the agreed depth and definition status in existing metadata or a brief line only when needed to prevent readers from mistaking an exploration for a final specification.

## Verify the saved result

- Re-read the affected files or fetch the affected Notion pages. Verify the actual saved content, location, title, structure, language, links, and relevant properties.
- Compare it with the current session contract and latest confirmed decisions. Ensure no unsupported requirements, excluded features, hidden assumptions, or obsolete statements remain in affected canonical sections.
- Verify that existing related documentation was reused or linked and that no duplicate source of truth was introduced. Reconcile affected summaries or indexes without modifying unrelated documents.
- For repositories, inspect the diff and run an existing relevant documentation or link check when available. For Notion, inspect the affected blocks, relationships, and links. Use checks proportionate to the change.
- If a correction reveals a genuine unresolved project decision, ask before writing a guessed resolution. Report blocked or unverified writes accurately.

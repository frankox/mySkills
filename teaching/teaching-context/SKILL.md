---
name: teaching-context
description: Resolve shared teaching context and retrieve teaching material from the School area in Notion. Use for teaching workflows that need the teacher's concepts, lessons, or assessments, including as a dependency of other teaching skills.
---

# Teaching Context

Provide the shared Notion context for the teacher's teaching workflows. Specialized teaching skills must load this skill before retrieving teaching sources and reuse its resolved context throughout the conversation.

## School is the source boundary

The teacher identifies the teaching area as **School** and has confirmed that this is the Notion wiki titled **Scuola**. It contains concepts or knowledge notes ("nozioni"), lessons ("lezioni"), and assessments ("verifiche"). These are content categories reported by the teacher, not verified database names or property names. Discover the actual hierarchy, labels, schemas, and relations rather than assuming three databases exist.

Confirmed references:

- Wiki root: [Scuola](https://app.notion.com/p/3dbf0f59020980c0b76ddf5b55afbae9).
- Root ID: `3dbf0f59-0209-80c0-b76d-df5b55afbae9`.
- Wiki data source: `collection://3def0f59-0209-8064-91c8-000becceb072`.

Use these references as the default entry point. Fetch the current root and data source before relying on their structure or querying them. School and Scuola refer to this same confirmed area; do not ask the teacher to reconfirm that name difference.

Use an available Notion connector or equivalent integration. This skill requires read access to the relevant School material. It does not require a particular connector's tool names.

1. Fetch the confirmed Scuola root above, unless the teacher explicitly supplies a replacement School URL or ID. Reuse the resolved context during the conversation.
2. If the root cannot be accessed, explain the retrieval limitation. When useful, search for School or Scuola and inspect candidate pages, databases, or teamspaces and their ancestry. If keyword search is inconclusive, inspect the relevant accessible sidebar or teamspace inventory when supported.
3. Resolve ambiguity before replacing the confirmed root. A similarly named area is not an automatic replacement. Ask for an updated link or access if the confirmed area remains inaccessible. Never create or rename an area to make it match.
4. Inspect the root's children and linked collections. Fetch current collection schemas before filtering or querying; discover how subjects, topics, classes, lessons, and assessments are represented. A linked collection can belong to the teaching area without being a direct child; verify that relationship.
5. Search within the resolved School hierarchy and its verified linked teaching collections. Do not silently use similarly titled material elsewhere in the workspace.

Keep the resolved root and useful collection URLs in conversation context. Do not invent IDs, persist a guessed binding in the skill, or rewrite the skill whenever a lesson changes.

## Retrieve relevant teaching evidence

- Reuse the subject, topic, class, and other constraints already provided. Ask only for missing information needed by the specialized workflow.
- Search relevant lessons by subject and topic, including meaningful synonyms, linked concepts, and applicable class or year filters. Follow relevant relations and read the lesson bodies; search snippets and titles alone do not establish coverage.
- Distinguish lesson evidence about what was taught from concept notes and previous assessments. Notes can explain a topic; an old assessment can inform format. Neither alone proves that the requested class studied that material.
- Note incomplete or truncated results, inaccessible pages, conflicting versions, and material gaps. An access or connector failure is not evidence that no lessons exist.
- If no relevant lessons are found after targeted searches and navigation, tell the teacher and request the topics, syllabus, notes, or lesson text directly. If that material is already supplied and sufficient, use it without asking again. For partial coverage, identify the missing topics and ask whether to supply or exclude them.
- Do not invent taught content or silently replace missing lesson evidence with generic knowledge or web research. Keep teacher-supplied coverage distinguishable from retrieved evidence.

## Return context to the teaching workflow

Provide a compact handoff containing:

- The verified School root and relevant collection links.
- Subject, topic, class or level when known, and requested artifact language.
- Relevant lesson links and a concise account of covered knowledge, practiced tasks, and expected level.
- Supporting concept notes or previous assessments, clearly identified by role.
- Gaps, retrieval limitations, teacher-supplied material, and unresolved decisions.

Use the user's or destination project's language for generated teaching artifacts. Preserve actual Notion titles, property names, and option values when referring to them. English skill instructions do not require English lessons or assessments.

This is a retrieval and context workflow. Preparing an assessment uses `teaching-assessment` when available. Creating or changing Notion content requires a user request that covers that write and a resolved destination; reading School does not authorize saving there. When a requested write creates a page directly in this wiki, follow the current connector's wiki rules: the verified connector requires the wiki page as a page parent rather than its data source as a database-item parent.

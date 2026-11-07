---
name: interview
license: Apache-2.0
description: Clarify a topic, goal, decision, or requirements through an adaptive conversation. Use when the user asks to be interviewed, when important ambiguity blocks useful work, or when project setup needs preference discovery. Works for software, research, writing, planning, and other topics without requiring a plan file.
---

# Interview

Help the user reach a useful understanding or decision. Match the depth and pace to the topic. Follow their stated preferences and applicable project instructions; do not turn every task into an interview.

## Prepare

- Identify the question being explored and the outcome the conversation should support.
- Read available context before asking for facts it already contains. If discovery tools are unavailable, state the gap and ask for the context that matters.
- Separate consequential unknowns from routine choices. Make reasonable, reversible implementation choices within the user's request.
- For a broad idea, start with a concrete example, desired outcome, and current pain points. For a narrow decision, focus on what changes the answer.

## Ask in useful rounds

Ask one to three related questions at a time by default, using fewer when an answer will shape the next question. Adapt to the user and the actual question interface's limits. Use ordinary conversation when no question tool is available.

- Make each question understandable on its own.
- Offer a recommendation when you have enough evidence, with its consequence and trade-off. Do not manufacture certainty.
- Use options for meaningful alternatives and free text for discovery. Leave room for a different answer.
- Show a sketch, example, or draft when it makes the choice concrete. Match the format to the available interface.
- Ask follow-up questions when an answer reveals an important gap. Do not impose a single-round limit on discovery.

Do useful independent work while answers are pending. Do not proceed with dependent work when the answer is required. Silence, elapsed time, or a preselected option is not an answer or authorization.

## Consolidate

Summarize confirmed decisions, assumptions, and remaining questions separately. Check the interpretation when a misunderstanding would matter; avoid a ritual approval round for routine summaries.

Return the result in the form the caller needs: a conversational conclusion, requirements, a decision record, setup preferences, or additions to an existing plan. Use a task-plan skill if helpful and installed, but do not require a plan or write files merely because an interview occurred.

Keep explicitly approved wording intact when the user has made exact wording a requirement. Ordinary drafting does not require a word-for-word approval table for every string.

## Revisit when needed

Accept corrections and update the affected conclusions. Explain a newly discovered constraint before asking the user to reconsider a settled choice.

A separate adviser can help a difficult decision when delegation is available, permitted, and worth its cost. Give it neutral context and distinguish its evidence from its judgment. Without that capability, examine alternatives directly and do not claim an independent opinion.

See [references/question-patterns.md](references/question-patterns.md) for examples.

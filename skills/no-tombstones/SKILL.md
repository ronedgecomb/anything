---
name: no-tombstones
license: Apache-2.0
description: Keep code, tests, comments, and documentation focused on current requirements. Use during ordinary creation, modification, review, and cleanup to prevent unnecessary residue of previous implementations, task narration, and redundant comments. Retain historical references and absence checks when they protect a concrete ongoing need.
---

# No tombstones

Document current behavior and test current requirements. A tombstone is material left behind or newly added mainly to describe or forbid a previous implementation, without serving a concrete ongoing purpose. The same applies to task narration—comments or prose added mainly to recount the current edit or fix rather than an ongoing reader need.

Apply this guidance during ordinary work within the requested scope. Respect review-only requests and preserve unrelated work. Existing tombstones can be addressed during an authorized review or cleanup; finding one does not expand the task.

## Documentation and comments

- Explain current behavior, supported usage, and constraints directly as timeless state. Revise or replace affected explanations in place instead of appending change-focused paragraphs or caveats.
- Omit prose that merely announces what changed or was removed, such as "This no longer uses the old parser" or "Inputs are now validated to prevent crashes." Keep a historical comparison only when the reader needs it to act or understand a current constraint.
- Write code comments to explain non-obvious invariants, constraints, external quirks, or trade-offs that the code cannot express on its own. Omit comments that paraphrase what the code already says, restate obvious control flow, narrate the current fix (such as `// Fix crash when header is empty`), or mark where deleted functionality used to be.
- Put fix rationale, transition context, and task narrative in commit messages, change summaries, or an existing place for migration guidance or decision history. Do not create a history document just to preserve removed material.

## Tests and verification

- Prefer tests of supported public behavior and current requirements. Keep meaningful regression coverage, including tests motivated by an old bug; name and assert the behavior they protect.
- Avoid permanent tests whose only purpose is proving that a removed filename, symbol, string, or implementation is absent. Removal alone does not establish a requirement for a new absence test.
- Keep an absence check when absence itself protects a concrete current contract. For example, an explicitly retired endpoint may be required to return `410 Gone`; test that observable response through its public interface.
- Establish the ongoing requirement from the request, project policy, supported contract, or other evidence. Speculation that an old implementation might return is insufficient justification.
- Temporary searches and diff inspection can verify a requested removal without becoming permanent tests. Match lasting coverage to the behavior that must continue to hold.
- When replacing a tombstone test, preserve any meaningful behavior it also covers. An assertion's negative form alone does not make it a tombstone.

## Code

Remove affected commented-out implementations, obsolete branches, and placeholder wrappers when their lack of a current consumer or requirement is established. Preserve required compatibility and verify consumers before removing an interface or shim.

Keep the resulting code coherent. Avoid leaving empty structures, misleading names, or explanatory remnants solely to mark the previous design.

## Keep history with a current purpose

Migration instructions, supported compatibility, operational constraints, decision rationale, and explicitly requested history can justify references to previous implementations. Identify the real purpose and keep the material proportionate. Apply established requirements without a new approval ritual; clarify only consequential uncertainty or conflicts.

Examples:

| Situation | Useful result |
| --- | --- |
| A storage implementation is replaced | Document current setup and usage; remove the affected stale instructions. |
| A private helper is deleted | Exercise the supported behavior and inspect remaining references during the change. |
| A bug is fixed | Keep a regression test for the required behavior; explain the fix in the commit or summary rather than adding fix-narrating comments or a README paragraph. |
| Code relies on a non-obvious external quirk | Add a concise comment explaining the constraint; omit comments that only paraphrase the code. |
| A retired endpoint is required to return `410 Gone` | Test that response through the public interface. |
| Users must migrate a supported older configuration | Keep the instructions needed for that migration in an appropriate existing location. |

## Check the result

For each affected explanation, comment, or assertion, identify the current requirement or reader need it serves. Someone unfamiliar with the previous implementation or the task that produced the change should be able to understand why ordinary documentation, comments, and tests exist.

Remove or rewrite material with no ongoing purpose, preserving useful coverage and required guidance. Verify the affected behavior, links, and references as appropriate. Report actual changes and checks in the task's normal completion summary; a separate report is optional.

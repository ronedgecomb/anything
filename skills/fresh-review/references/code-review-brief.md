# Code review brief

Use this when the artifact is code. Fill or remove each placeholder. Provide actual source content when the reviewer cannot access a repository.

```text
Review <artifact, change, or accessible snapshot> against <requested outcome>.
Context: <the relevant behavior and applicable project rules>.
Comparison, if available: <the resolved base and target, or an explicit diff>.
Other relevant inputs: <accessible source, tests, or decisions>.

Review without changing the artifacts. Run only <permitted checks>, respecting <shared-resource and environment limits>.

Look for:
- Concrete correctness failures and regressions in the affected behavior.
- Missing or misleading verification of a claimed result.
- Data, concurrency, compatibility, and security issues relevant to this change.
- Inconsistent interfaces, duplicated rules, or complexity with a practical cost.
- Tests that duplicate coverage without useful confidence or depend on incidental implementation details, making harmless changes fail.
- Requirements that the artifact misses, and assumptions that need evidence.

Return findings by importance. For each, identify the source location, a reproducible or well-supported failure scenario, and a proportionate fix. Distinguish confirmed defects from questions and preferences.

Favor the smallest clear, complete correction that fits project conventions. Recommend broader changes or extra tests when they address a concrete requirement, failure, or risk.

State what you inspected, checks actually performed, and material limits. Do not assume the author's interpretation or proposed design is correct.
```

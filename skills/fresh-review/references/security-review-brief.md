# Security review brief

Use when the change or artifact has meaningful security, privacy, or abuse implications. A dedicated reviewer is optional unless the task or project requires one.

```text
Review <artifact or accessible snapshot> for the security and privacy consequences of <requested outcome>.

Context:
- Assets and data involved: <relevant items>.
- Actors and trust boundaries: <who can cause which effects>.
- Environment and exposure: <known facts, with unknowns labeled>.
- Applicable constraints: <project rules and explicit decisions>.

Preserve the artifacts. Run only <permitted checks> and avoid <shared resources or side effects>.

Check the risks that apply:
- Authentication, authorization, and unintended access or state changes.
- Untrusted input reaching interpreters, storage, redirects, or privileged actions.
- Sensitive data in output, logs, retention, and deletion paths.
- Resource abuse and unintended costs.
- Differences between intended and actual deployment or execution conditions.

For each finding, give its severity, evidence location, attacker or failure actor, steps, concrete consequence, and whether it is exploitable under known conditions. Distinguish demonstrated exposure from assumptions. Suggest a fix and cite an authoritative reference when useful.

State the reviewed snapshot, checks actually run, and remaining limits. Do not assume an approved design is secure, or treat uncertainty alone as proof of a vulnerability.
```

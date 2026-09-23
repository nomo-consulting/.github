# Organization Work Management Standard

- Status: Approved
- Version: 1.0
- Updated: 2026-09-23

## Purpose

This standard defines how Nomo Consulting uses GitHub issues, pull requests, Projects, and milestones across repositories.

Repository-specific rules may extend or override this standard when the exception is documented in that repository.

## Operating model

- Issues describe verifiable outcomes.
- Pull requests are the preferred way to resolve issues and provide implementation evidence.
- Projects organize workflow and portfolio views without duplicating issue metadata.
- Milestones represent verifiable delivery outcomes.
- SOWs and canonical project context remain the authority for scope and approved decisions.

## Shared taxonomy

### Issue types

- `Task`: Documentation, context, configuration, maintenance, or other repository work.
- `Bug`: Correction of unintended behavior.
- `Feature`: New user-facing or operational capability.
- `Solution Design`: Architecture, implementation approach, or technical design work that produces a versioned design artifact.

### Project status

- `Todo`
- `In progress`
- `Blocked`
- `Done`

Status is Project-scoped. An issue should move to `Done` when its acceptance criteria are met and it is closed, normally by merging its resolving pull request.

### Organization issue fields

- `Priority`: `Urgent`, `High`, `Medium`, or `Low`.
- `Start date`: Set only after scheduling is confirmed.
- `Target date`: Set only after scheduling is confirmed.
- `Domain`:
  - `Strategy`
  - `Design`
  - `Frontend`
  - `Backend`
  - `DevOps`
  - `Data`
  - `Marketing`
  - `Operations & Finance`
- `Blocked by`: `None`, `Client`, `Vendor`, or `Internal`.
- `Blocking reason`: A short text explanation of the current blocker and the next action required to unblock it.

When an issue is `Blocked`, `Blocked by` and `Blocking reason` must both be populated. Clear both when the issue is unblocked; the issue timeline retains the change history.

Effort is not part of this operating model. Do not delete an existing organization field until its usage across repositories and Projects has been audited.

### Labels

Use labels only for a concrete required action that is not already represented by Type, Domain, Status, Priority, or milestone:

- `needs:input`: Missing information, content, assets, or access.
- `needs:approval`: An explicit decision or sign-off is required.
- `needs:deployment`: A release or environment action is required.

Use one of these labels only while the need is current. Repositories may define additional domain-specific labels, but must not recreate shared fields as labels.

### Language

- Shared types, fields, statuses, labels, and milestone conventions use English.
- Issue and pull-request content may use the project's working language.

## Issue creation standard

### Preferred repository outcome

Strongly prefer creating a repository issue when the expected outcome is a versioned change to:

- Code or tests.
- Canonical context, documentation, or decision records.
- Repository configuration, dependencies, CI/CD, templates, or workflows.

This preference is not a blocker. An operational issue without a repository change is allowed when it still has a concrete outcome, verifiable acceptance criteria, a clear owner, and durable completion evidence. Use a Project draft item for temporary reminders, meetings, follow-ups, or exploratory discussion that do not yet meet that threshold.

External operational work should produce a repository artifact when practical, such as configuration-as-code, a runbook, a decision record, or secret-safe verification evidence.

### Definition of ready

Before work begins, an issue must have:

- A repository and expected outcome.
- An issue type, Domain, Priority, and assignee.
- Clear scope, acceptance criteria, and validation expectations.
- A completed duplicate check.
- Known dependencies or blockers recorded.
- A scope normally suitable for one coherent pull request.

Start and target dates are required only after scheduling is confirmed. A milestone is required only after the delivery outcome has been selected.

### Required issue content

- **Outcome:** The concrete result expected.
- **Context:** Why the change or outcome is needed.
- **Scope:** What is included.
- **Acceptance criteria:** Verifiable conditions for completion.
- **Validation:** Tests or evidence required from the resolving pull request or operator.
- **Dependencies:** Related issues, systems, or required inputs.
- **References:** Relevant SOW, context, design, or incident material.
- **Out of scope:** Include only when needed to protect the boundary.

Issue titles should state the outcome without type, domain, or workflow prefixes. For example, use `Add quote-request validation`, not `Feature: Add quote-request validation`.

### Definition of done

- The resolving pull request is merged, or an approved operational exception has durable completion evidence.
- Acceptance criteria are satisfied.
- Validation evidence is recorded.
- Tests and documentation are updated where applicable.
- Canonical context is updated when behavior or decisions changed.
- The issue is closed as completed.

Close an issue as not planned when it is rejected, obsolete, or a duplicate. Do not present it as delivered.

## Pull-request standard

### Relationship to issues

One issue should normally map to one coherent pull request. A pull request may resolve multiple issues only when:

- The changes are technically inseparable.
- They share the same validation and rollback boundary.
- Reviewing them together remains clear.
- Every linked issue's acceptance criteria are fully satisfied.

Use one complete closing reference for every issue fully resolved by the pull request:

```text
Closes #12
Closes #15
Closes nomo-consulting/another-repo#8
```

Use `Refs #12` for a partial or supporting pull request. Only the final resolving pull request should use `Closes`, `Fixes`, or `Resolves`.

GitHub processes closing keywords when a pull request targets and merges into the repository's default branch. See [Linking a pull request to an issue](https://docs.github.com/en/issues/tracking-your-work-with-issues/using-issues/linking-a-pull-request-to-an-issue).

### Pull-request requirements

- Keep one coherent outcome per pull request.
- Open a draft pull request until it is ready for review.
- Summarize the outcome and material changes.
- Link all resolved and referenced issues.
- Provide validation evidence and screenshots when applicable.
- Identify material risks and rollback steps.
- Update tests, documentation, and canonical context when required.
- Never include credentials, secrets, or sensitive client data.

Pull requests should not be added to a Project when their linked issues already represent the work. The linked issue is the Project item and closes when the resolving pull request merges.

## Milestone convention

- `01 - Setup & Discovery Complete`
- `02 - Solution & Design Approved`
- `03 - Implementation Complete`
- `04 - Validation Complete`
- `05 - Launch Ready`
- `06 - Delivery & Handover Complete`

Projects may omit milestones that do not apply while preserving the numbering of those they use. Store schedule dates in milestone due dates rather than milestone titles.

## Governance

- Apply taxonomy changes idempotently and validate existing usage before deleting fields or labels.
- Do not migrate an existing Project without an explicit item-by-item mapping and reconciliation.
- Keep Project automation one-way from issue lifecycle to Project status; setting a Project item to `Done` must not close an issue by itself.
- Review this standard when GitHub changes the capabilities of issue fields, issue forms, or Projects.

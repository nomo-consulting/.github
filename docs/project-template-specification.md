# Organization Project Template Specification

- Status: Approved
- Version: 1.0
- Updated: 2026-09-23

## Template purpose

Create one organization Project template for delivery work. It standardizes workflow and views while keeping issue metadata on organization issues.

This specification documents GitHub configuration. The Project template itself must be created in the organization's GitHub Projects settings.

## Fields

### Project-scoped

- `Status`: `Todo`, `In progress`, `Blocked`, `Done`.

### Organization issue fields displayed in the Project

- Type
- Priority
- Start date
- Target date
- Domain
- Blocked by
- Blocking reason

### GitHub system fields displayed when useful

- Assignees
- Milestone
- Labels
- Repository
- Parent issue
- Sub-issues progress

Do not add a duplicate Project-scoped Priority, Domain, date, or blocking field.

## Views

### Backlog

- Layout: Table.
- Exclude completed items.
- Group by Milestone when milestones are assigned.
- Sort by Priority and then Target date.

### Active Board

- Layout: Board.
- Group by Status.
- Exclude `Done`.

### Roadmap

- Layout: Roadmap.
- Use Start date and Target date.
- Group by Milestone when useful.

### Blocked

- Layout: Table.
- Filter to `Status = Blocked`.
- Display assignee, Blocked by, Blocking reason, and Target date.

### Needs Triage

- Layout: Table.
- Show issues missing an assignee, Priority, Domain, or type.
- Do not treat missing dates or milestones as triage failures before scheduling is confirmed.

Projects may add views for a specific client or delivery model without changing the shared field definitions.

## Workflows

Enable:

- Set Status to `Todo` when an issue is added.
- Set Status to `Done` when an issue is closed as completed.
- Return Status to `Todo` when an issue is reopened.
- Auto-add repository issues using an `is:issue` filter configured separately for each Project.

Do not enable:

- Closing an issue when its Project Status changes to `Done`.
- Auto-adding pull requests when their linked issues already represent the work.
- Automation that overwrites populated organization issue fields.

Auto-add workflows are not copied with GitHub Project templates and must be configured for each Project after creation.

## Milestones

Create only the milestones that apply:

- `01 - Setup & Discovery Complete`
- `02 - Solution & Design Approved`
- `03 - Implementation Complete`
- `04 - Validation Complete`
- `05 - Launch Ready`
- `06 - Delivery & Handover Complete`

Each milestone must describe a verifiable result and use GitHub's due-date field when a target date is confirmed.

## Project initialization checklist

- Create the Project from the organization template.
- Link the Project to its repository and responsible team.
- Configure the repository-specific issue auto-add workflow.
- Confirm organization issue fields are visible.
- Create only applicable milestones.
- Confirm default views and filters.
- Add or migrate issues using an explicit mapping.
- Reconcile counts, statuses, fields, dates, milestones, and assignees.
- Confirm pull requests are not duplicated as Project items.

# Project-Specific AI Engineering Rules

**Document:** `PROJECT_RULES.md`  
**Version:** `1.2.0`  
**Purpose:** Record the verified technical reality, conventions and commands of this repository.

> `UNIVERSAL_RULES.md` defines **how the agent works**. This file defines **what the agent should work with in this project**.

---

## 1. Project Identity

- **Project Name:** `<project-name>`
- **Description:** `<short description>`
- **Repository:** `<repository name or URL if appropriate>`
- **Primary Branch:** `<main/master/develop/etc>`
- **Application / Package ID:** `<if applicable>`
- **Target:** `<web/mobile/backend/desktop/embedded/etc>`
- **Status:** `<active/maintenance/experimental/etc>`

### Discovery Metadata

- **Last Discovered:** `<YYYY-MM-DD HH:mm>`
- **Discovered By:** `<agent>`
- **Repository Revision:** `<commit hash or unknown>`
- **Configuration Status:** `VERIFIED / PARTIALLY_VERIFIED / NEEDS_HUMAN_INPUT`

---

## 2. Technology Stack

| Area             | Technology | Version | Source   | Status              |
| ---------------- | ---------- | ------- | -------- | ------------------- |
| Language         | `<...>`    | `<...>` | `<file>` | `VERIFIED`          |
| Framework        | `<...>`    | `<...>` | `<file>` | `VERIFIED`          |
| Frontend         | `<...>`    | `<...>` | `<file>` | `VERIFIED/OBSERVED` |
| Backend          | `<...>`    | `<...>` | `<file>` | `VERIFIED/OBSERVED` |
| Database         | `<...>`    | `<...>` | `<file>` | `VERIFIED/OBSERVED` |
| State Management | `<...>`    | `<...>` | `<file>` | `OBSERVED/DECLARED` |
| Testing          | `<...>`    | `<...>` | `<file>` | `VERIFIED/OBSERVED` |
| Build            | `<...>`    | `<...>` | `<file>` | `VERIFIED`          |
| CI/CD            | `<...>`    | `<...>` | `<file>` | `VERIFIED/OBSERVED` |
| Hosting          | `<...>`    | `<...>` | `<file>` | `VERIFIED/OBSERVED` |
| Other            | `<...>`    | `<...>` | `<file>` | `VERIFIED/OBSERVED` |

Only facts supported by evidence or an explicit project decision may be recorded.

### Dependency Policy

- **Package Manager:** `<npm/pnpm/yarn/bun/pub/gradle/etc>`
- **Lock File:** `<file>`
- **Approved Sources:** `<if any>`
- **Update Policy:** `<project-specific policy>`

---

## 3. Architecture

### 3.1 Official Architecture

- **Pattern:** `<...>`
- **Status:** `DECLARED / VERIFIED / OBSERVED`
- **Source / ADR:** `<file/reference>`

`OBSERVED` means visible in code. `DECLARED` means explicitly defined by the project. `VERIFIED` means evidence confirms the documented configuration.

### 3.2 Module / Layer Structure

```text
<project-root>
├── <module/layer>
│   ├── <submodule>
│   └── ...
└── ...
```

### 3.3 Dependency Direction

```text
<allowed dependency flow>
```

### 3.4 State Management

- **Pattern:** `<...>`
- **Library:** `<...>`
- **Source:** `<file>`
- **Status:** `VERIFIED/OBSERVED/DECLARED`

### 3.5 Data Access / Integration

- **Pattern:** `<repository/service/DAO/etc>`
- **Database Access:** `<...>`
- **API Client:** `<...>`
- **Caching:** `<...>`

### 3.6 Error Handling

- **Error Model:** `<...>`
- **User-facing Handling:** `<...>`
- **Logging:** `<...>`

### 3.7 Authentication / Authorization

- **Authentication:** `<...>`
- **Authorization:** `<...>`
- **Session / Token:** `<...>`
- **Source:** `<file/reference>`
- **Status:** `VERIFIED/OBSERVED/DECLARED`

Do not infer business, security or compliance policy from implementation alone.

---

## 4. Testing Strategy

- **Unit Tests:** `<tool/path>`
- **Integration Tests:** `<tool/path or N/A>`
- **E2E Tests:** `<tool/path or N/A>`
- **UI / Widget Tests:** `<tool/path or N/A>`
- **Coverage Tool:** `<tool or N/A>`
- **Required Threshold:** `<value or N/A>`
- **Test Data Strategy:** `<description>`

Test selection should follow the affected behavior and risk.

---

## 5. Required Commands

Commands must come from repository configuration. Never invent them.

| Purpose          | Command     | Source   | Status                            | Notes   |
| ---------------- | ----------- | -------- | --------------------------------- | ------- |
| Install          | `<...>`     | `<file>` | `VERIFIED/UNVERIFIED/UNKNOWN`     | `<...>` |
| Format           | `<...>`     | `<file>` | `VERIFIED/UNVERIFIED/UNKNOWN/N/A` | `<...>` |
| Lint             | `<...>`     | `<file>` | `VERIFIED/UNVERIFIED/UNKNOWN/N/A` | `<...>` |
| Type Check       | `<...>`     | `<file>` | `VERIFIED/UNVERIFIED/UNKNOWN/N/A` | `<...>` |
| Unit Test        | `<...>`     | `<file>` | `VERIFIED/UNVERIFIED/UNKNOWN/N/A` | `<...>` |
| Integration Test | `<.../N/A>` | `<file>` | `VERIFIED/UNVERIFIED/UNKNOWN/N/A` | `<...>` |
| E2E Test         | `<.../N/A>` | `<file>` | `VERIFIED/UNVERIFIED/UNKNOWN/N/A` | `<...>` |
| Build            | `<...>`     | `<file>` | `VERIFIED/UNVERIFIED/UNKNOWN`     | `<...>` |
| Development      | `<...>`     | `<file>` | `VERIFIED/UNVERIFIED/UNKNOWN/N/A` | `<...>` |
| Production Build | `<.../N/A>` | `<file>` | `VERIFIED/UNVERIFIED/UNKNOWN/N/A` | `<...>` |

```text
VERIFIED   = reliable source found and command successfully executed
UNVERIFIED = reliable source found but execution not yet confirmed
UNKNOWN    = no reliable source found
N/A        = category does not apply
```

---

## 6. Code Conventions

- **Naming:** `<...>`
- **Formatting:** `<formatter/config>`
- **Comments / Docs:** `<...>`
- **Logging:** `<logger/policy>`
- **Component/File Conventions:** `<...>`

---

## 7. UI / UX Conventions

- **Design System:** `<...>`
- **Component Library:** `<...>`
- **Typography:** `<...>`
- **Color Tokens:** `<...>`
- **Spacing:** `<...>`
- **Responsive Rules:** `<...>`
- **Accessibility:** `<...>`

Do not change an established design system without the approval required by `UNIVERSAL_RULES.md`.

---

## 8. API / External Integrations

- **API Style:** `<REST/GraphQL/gRPC/etc>`
- **Client:** `<...>`
- **Base URL Configuration:** `<...>`
- **Serialization:** `<...>`
- **Retry / Timeout:** `<...>`
- **Error Mapping:** `<...>`
- **External Services:** `<list>`

Breaking contract changes remain subject to universal approval rules.

---

## 9. Database

- **Database:** `<...>`
- **Schema Location:** `<...>`
- **Migration Tool:** `<...>`
- **Migration Policy:** `<...>`
- **Seed Data:** `<...>`
- **Index Strategy:** `<...>`

Never record credentials or secrets here.

---

## 10. Environment / Secrets

- **Environment Files:** `<...>`
- **Secret Provider:** `<...>`
- **Local Setup:** `<...>`
- **Production Secret Handling:** `<...>`

Only describe the mechanism; never store secret values.

---

## 11. Build / Deployment

- **Build Targets:** `<...>`
- **Deployment Platform:** `<...>`
- **CI Workflow:** `<path>`
- **CD Workflow:** `<path/N/A>`
- **Release Process:** `<...>`
- **Production Approval:** `<...>`

Deployment remains subject to universal approval policy.

---

## 12. Git Workflow

- **Primary Branch:** `<...>`
- **Branch Prefixes:** `<...>`
- **Commit Convention:** `<...>`
- **PR Requirement:** `<...>`
- **Required Checks:** `<...>`

This section may add project requirements but may not weaken universal branch/merge rules.

---

## 13. Important Files / Entry Points

| Purpose             | Path                 | Source / Notes                                                        |
| ------------------- | -------------------- | --------------------------------------------------------------------- |
| App Entry           | `<path>`             | `<...>`                                                               |
| Main Config         | `<path>`             | `<...>`                                                               |
| Dependency Manifest | `<path>`             | `<...>`                                                               |
| Test Config         | `<path>`             | `<...>`                                                               |
| Build Config        | `<path>`             | `<...>`                                                               |
| CI                  | `<path>`             | `<...>`                                                               |
| Deployment          | `<path>`             | `<...>`                                                               |
| Development Log     | `DEVELOPMENT_LOG.md` | Canonical activity data only; format governed by `UNIVERSAL_RULES.md` |

Only verified paths belong here.

---

## 14. Skills / MCP / External Tools

### Skills

```text
- `<skill>`
- `<skill>`
```

### MCP / Tools

| Tool     | Purpose     | Access         | Required   | Source        |
| -------- | ----------- | -------------- | ---------- | ------------- |
| `<tool>` | `<purpose>` | `<read/write>` | `<Yes/No>` | `<reference>` |

Never infer tool capabilities from a name alone.

---

## 15. Constraints and Non-Goals

### Constraints

```text
- `<durable project constraint>`
- `<durable project constraint>`
```

### Non-Goals

```text
- `<explicit non-goal>`
- `<explicit non-goal>`
```

Use these to prevent scope creep.

---

## 16. Project Discovery Protocol

### Trigger

The agent MUST run the onboarding discovery procedure **before implementation work** when any of these is true:

- this file is newly introduced,
- core sections still contain placeholders,
- `Configuration Status` is not `VERIFIED`,
- repository evidence may have materially changed,
- the user explicitly requests project onboarding/discovery.

If the file is already current and verified, do not perform a full discovery at the start of every task; perform targeted discovery for the affected area.

### Procedure

```text
1. Inspect Git/repository baseline.
2. Inspect package/dependency manifests and lock files.
3. Inspect build and tool configuration.
4. Inspect test configuration.
5. Inspect source tree and entry points.
6. Inspect docs / ADRs.
7. Inspect CI/CD and deployment configuration.
8. Compare findings with this file.
9. Update only evidence-backed fields.
10. Verify critical commands when safe and practical.
11. Record unresolved conflicts/unknowns.
12. Update Discovery Metadata.
```

### Evidence Rules

- Prefer concrete repository evidence over inference.
- Record `Source` for important facts.
- Keep `OBSERVED` separate from `DECLARED` decisions.
- Never invent commands, versions, architecture, policies or production behavior.
- If evidence conflicts and intent is unclear, do not choose silently; record the conflict and request clarification.

### Safe Self-Update

The agent MAY update this file during discovery. Updates must be targeted, evidence-backed, durable, secret-free and limited to project configuration. Do not rewrite unrelated sections.

---

## 17. Maintenance Protocol

Update this file when durable project reality changes, including framework/language, major dependencies, commands, architecture, CI/CD, conventions, tools or important paths.

Do not update it for every small implementation change.

For meaningful updates, record:

```text
What changed:
Why:
Source:
Status:
Date:
```

---

## 18. Architecture Decision Records

- **ADR Location:** `<path or N/A>`
- **ADR Convention:** `<format or N/A>`

Repository observations are not official architecture decisions unless supported by an explicit decision or ADR.

---

## 19. Project-Specific Definition of Done

Add only checks genuinely required for this repository:

```text
[ ] <project-specific check>
[ ] <project-specific check>
[ ] <project-specific check>
```

Universal completion requirements remain mandatory.

---

## 20. Configuration Integrity

Entries may be `VERIFIED`, `OBSERVED`, `DECLARED`, `UNVERIFIED`, `UNKNOWN` or `N/A`.

Do not label facts `VERIFIED` or `DECLARED` without evidence.

If repository evidence conflicts with this file:

1. inspect the current state,
2. determine the current technical reality,
3. correct the file when intent is unambiguous,
4. otherwise request human clarification.

---

## 21. Do Not Invent

Never invent framework/package versions, commands, architecture decisions, schema, API contracts, CI/CD providers, tool capabilities, security policies, business rules, compliance requirements or production configuration.

---

## 22. Development Log Relationship

`DEVELOPMENT_LOG.md` is a data-only activity file. It must contain actual project entries only; its schema, formatting rules and write procedure are defined exclusively by `UNIVERSAL_RULES.md`.

## 22. Final Principle

> **This file records the project's durable technical reality. `UNIVERSAL_RULES.md` governs how the agent must work within it.**

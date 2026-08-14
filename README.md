# AI Coding Agent Rules & Workflow System

[🇹🇷 Türkçe](https://github.com/smetcan/universal-agent-rules/blob/main/README_TR.md) | [🇬🇧 English](https://github.com/smetcan/universal-agent-rules/blob/main/README.md)

Rule and workflow documents developed out of my own needs to govern and discipline AI coding agents (Gemini, Claude, Cursor, Copilot, etc.) across various software projects.

## Why I Created This

While working across different projects, maintaining separate rule files (`AGENTS.md`, `RULES.md`, `GEMINI.md`) for each repository eventually turned into a chaotic mess. I would forget to port a good rule tested in one project to another, or rule files would grow uncontrollably.

I realized that:

- Some rules were strictly project-specific (stack, versions, executable commands).

- Other rules were universal engineering practices that remained unchanged regardless of language or framework (Git workflows, security, human approvals, error handling).

To consolidate this fragmentation, I gathered my own custom rule files and spent hours iterating with AI models—refining, testing, and stress-testing them through numerous prompts—until this dual-rule architecture matured. I am continuously striving to improve my own workflows, and I use this system actively in my daily work. I wanted to share it publicly in hopes that it helps others too.

## Architecture

The system consists of three main files that separate responsibilities clearly:

1. **`UNIVERSAL_RULES.md`:** Technology-agnostic constitution. Dictates how the agent behaves, communicates with the human developer, maintains code quality, handles Git branches, and enforces security.

2. **`PROJECT_RULES.md`:** The technical identity card of the repository. Records verified frameworks, real commands, and architectural layers to prevent hallucinations.

3. **`DEVELOPMENT_LOG.md`:** Machine- and human-readable journal tracking completed work for transparency and auditability.

4. **`GEMINI.md` / `AGENTS.md`:** Main entry point linking `@./UNIVERSAL_RULES.md` and `@./PROJECT_RULES.md` into the IDE system prompt.

## Rule Summary

Here is a quick overview of what these files contain and the constraints they enforce on AI agents:

### 1. `UNIVERSAL_RULES.md` (Behavior & Quality Constitution)

- **Ask First:** Requires explicit human approval before adding third-party packages, modifying database schemas, altering design systems, or introducing breaking API changes.

- **No Guessing:** Forbids guessing file paths, signatures, or data models. Requires inspecting source code before writing changes.

- **No Band-Aid Fixes:** Prohibits swallowing errors with empty `try/catch` blocks, using fake fallback data to pass tests, or suppressing type errors with `@ts-ignore` / `any`. Requires identifying root causes.

- **Git Discipline:** Opens dedicated feature/fix branches (`feat/`, `fix/`, etc.). Never merges to primary branches without explicit human testing and approval.

- **Context Isolation:** If an active branch is unmerged and a new task is requested, the agent proactively recommends completing or stashing the current branch before opening a clean branch for the new context.

- **Security:** Hardcoded API keys or secrets are strictly forbidden; enforces `.env` configurations.

### 2. `PROJECT_RULES.md` (Project Reality)

- **Truth Statuses (`VERIFIED`, `OBSERVED`, `DECLARED`, `UNVERIFIED`):** Categorizes project facts by confidence level to eliminate assumptions.

- **Verified Commands:** Only allows executing commands explicitly defined in repository manifests.

- **Discovery Protocol:** Runs onboarding inspections on project manifests (`package.json`, `pubspec.yaml`, etc.) to document reality automatically.

### 3. `DEVELOPMENT_LOG.md` (Development Journal)

- **Fixed Anchor Schema:** Records date, type, status, branch, base branch, commit hash, and summary in a strict format.

- **Clean Log Principle:** Logs only meaningful architectural or feature work; routine file reads or searches are ignored.

**Note:** In clause `16.3` of the `UNIVERSAL_RULES.md` document, the default language for the `DEVELOPMENT_LOG.md` file is set to **Turkish**. Feel free to change it according to your preference.

## Limitations & Drawbacks

While this system has significantly smoothed my development workflow, it is not a silver bullet. Here are some honest limitations I experienced:

- **Context Window Overhead:** Detailed rule files consume a portion of the prompt context window, which can reduce available context during very long chat sessions.

- **Initial Onboarding Friction:** Running the initial discovery protocol on an existing codebase can take a few minutes before code changes begin.

- **Over-Engineering for Small Scripts:** For simple single-file scripts or quick experiments, enforcing this level of Git and logging discipline can feel overly bureaucratic.

- **Agent Drift:** AI models can still occasionally drift or ignore instructions during lengthy sessions. Human oversight remains essential.

## How to Use

1. Copy **`UNIVERSAL_RULES.md`** to your project root.

2. Copy **`PROJECT_RULES.md`** to your project root.

3. Create your entry file (`GEMINI.md`, `.cursorrules`, or `AGENTS.md`) referencing both rule files (`@./UNIVERSAL_RULES.md`, (`@./PROJECT_RULES.md`).

4. Execute one of the starter prompts below to initiate the workflow.

## Starter Prompts

### 1. Existing Project Onboarding

```
Perform first-time onboarding in this repository.

Execute the discovery protocol in PROJECT_RULES.md step-by-step,
inspect the repository, and update PROJECT_RULES.md using ONLY
verifiable evidence.

Do NOT make any code changes.
```

### 2. Greenfield Project Setup

```
We are starting a new greenfield project.

First, gather the necessary project requirements and technical decisions from me.

Do NOT make any assumptions about framework, architecture, database, state management, or tooling.

Record the agreed information in PROJECT_RULES.md marked as DECLARED.

Do NOT begin implementation until the initial technical plan is established and approved.
```

## Contributing

I am constantly learning and refining these workflows. If you find inconsistencies, missing edge-cases, or room for improvement, feel free to open an Issue or submit a Pull Request. Feedback and shared experiences are always welcome!

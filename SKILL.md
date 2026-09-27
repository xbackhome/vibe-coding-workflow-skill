---
name: vibe-coding-workflow
description: Use when starting or continuing a software product with AI coding, especially when an idea is vague, a feature needs scoping, or an existing project risks scope drift and accumulating complexity. Guides discovery, implementation, verification, and iteration at a depth proportional to the task.
---

# Vibe Coding Workflow

Turn a product idea or feature request into small, observable increments. Keep the user's goal and constraints authoritative. Choose the lightest process that still exposes consequential decisions and proves the result works.

## Choose the path

| Situation | Working path |
| --- | --- |
| Small, well-defined change in an existing project | Inspect relevant code and rules → state expected behavior → change → verify → report. |
| New product or substantial feature | Clarify outcome and boundaries → scout existing projects → write a brief spec → check repository constraints → plan a vertical slice → implement and verify → iterate. |
| Exploratory prototype with uncertain demand | Identify the one assumption to test → build the smallest runnable experiment → observe a real user or realistic usage → revise or discard. Record decisions only when they will matter later. |

Do not turn a small change into a document-heavy project. If the user has already supplied a clear spec, use it instead of restarting discovery. When the user requests implementation, continue through the authorized work; ask only for missing decisions that materially change the result.

## Select tools by need

Use [the task-based tool map](references/tool-map.md) when the user asks which tools to use or when a tool materially improves the current stage. It covers ChatGPT Deep Research for evidence gathering, Google Stitch for UI exploration, Cursor and other coding agents for implementation, browser or computer control for verification, and optional Superpowers or Matt Pocock Skills workflows. Choose available capabilities for the job; mentioning a tool does not authorize installing it. Verify current capabilities before making a tool-specific recommendation.

## 1. Establish the outcome

Capture who uses the product, the problem, the core user journey, the delivery surface, and what a successful first use looks like. Identify non-negotiable constraints early: platform, deployment, offline or data residency needs, integrations, budget, and accessibility where relevant. Separate known facts, assumptions, and open decisions.

When demand is uncertain, research the intended users, alternatives, and actual workflows before settling the first release. Distinguish observed evidence from guesses. For an interface-heavy product, sketch or prototype the main flow and agree on visual references or interaction behavior before asking an agent to build the UI.

If several external sources must be synthesized, ChatGPT Deep Research can produce a sourced research report; a normal conversation is enough for quick clarification. For UI-heavy work, Google Stitch can help explore screens and a coding agent such as Cursor can implement an approved design. Compare the running UI with the design and verify interaction behavior; never promise a literal 1:1 result from a handoff alone.

For a new product or major technical choice, search for close open-source precedents before recommending a build path. Inspect upstream functionality, maintenance, license, and fit with the stated constraints. Recommend whether to adopt, adapt, reference, or build. If `project-open-source-scout` is available and applicable, follow it. Do not present an invented shortlist when the idea is still unspecified.

## 2. Define the first slice

Resolve ambiguous core terms before detailed questioning. Write a brief, durable spec with:

- User outcome and main workflow.
- In-scope behavior and explicit exclusions for this slice.
- Business rules, material error cases, and acceptance examples.
- Constraints that implementation must obey.
- Open decisions that genuinely block implementation.

Ask focused questions, preferably with concrete options. Periodically check whether unresolved items would change the implementation or acceptance result. Stop questioning when the core path, key boundaries, and contradictions are resolved. Do not use a fixed question quota.

For a maintained product, the approved spec is the source of truth. Propose changes to it when reality contradicts it; do not silently rewrite requirements or add features. For a throwaway experiment, a few acceptance examples may be enough. Use [the working note template](references/working-note.md) when the work spans multiple sessions or has several decisions to preserve.

## 3. Inspect the project and plan

Read applicable `AGENTS.md`, `CONTEXT.md`, ADRs, conventions, and the relevant code path. Search for existing implementations and reusable utilities. Compare the new spec with existing constraints and surface any conflict before implementation.

For a new repository, establish Git history and a repeatable way to run the product. Record required configuration without committing credentials or private data. Make sure the agent can exercise the feature it is about to build; if the environment cannot run it, state that limitation in the plan.

Choose technology after understanding the required behavior and environment. Favor the simplest design that meets current needs. Explain material trade-offs; leave routine implementation choices to the agent. Plan one runnable vertical slice at a time, with expected behavior and a verification method. Keep progress and confirmed decisions in files when a long session or context compression would otherwise lose them.

## 4. Implement without scope drift

Change only what the current slice requires. Reuse existing conventions and capabilities. Avoid duplicate utilities, speculative abstractions, and fallback values or exception handling that conceal broken assumptions. Keep the data flow readable. If an implementation reveals a requirement conflict, report it and resolve the decision before expanding scope.

Do not treat an external package, starter repository, plugin, or skill as automatically approved for installation merely because it was found during research. Check its license and follow the environment's required security or approval process before adopting it.

## 5. Verify, review, and iterate

Run the smallest meaningful checks available for the changed behavior. Use a real workflow or UI inspection when the feature is interactive. Distinguish what was executed from what remains unverified; never claim success from code inspection alone. Ask the user to exercise the result when their judgment or access is necessary for acceptance.

Give the coding agent browser or computer interaction when the feature requires visual or end-to-end checks and such access is available. Use existing built-in capabilities first; install an additional browser or computer-use plugin only when needed and permitted by the environment.

Review the diff against the spec and project conventions: missing behavior, extra behavior, duplicated code, unnecessary defensive logic, excess abstraction, and unclear naming. When verification fails, diagnose the cause before layering on fixes. Update the working note or spec only for decisions that changed. Create a Git commit at a verified functional milestone if that fits the project's version-control workflow; do not require a commit after every edit.

## Completion report

State what the user can now do, what changed, what was verified and how, and any remaining limitation or decision. A feature is done when its agreed acceptance behavior has been observed, relevant checks have passed or limitations are explicit, and the user can inspect the result.

## Example start

> I want a personal desktop reader that imports UTF-8 TXT files. First establish the core reading flow and first-release boundaries, then look for close open-source readers and recommend adopt, adapt, or build. Check this repository's rules before choosing a stack. Implement one runnable slice, show the verification evidence, and keep decisions in a short working note.

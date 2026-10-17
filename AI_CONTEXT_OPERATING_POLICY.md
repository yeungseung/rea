# AI Context & Documentation Operating Policy

Status: repository-wide operating rule for long-running AI-assisted work.

## Purpose

This repository may accumulate research, design, implementation, audit, evidence, handoff, and merge documents over long periods. The goal is **not to reduce necessary documentation**. The goal is to prevent an AI agent from rereading the whole project history in every session.

The core rule is:

> **The repository may be large. The always-visible AI context must stay small. Load depth only when the current task requires it.**

This policy follows four proven patterns:

1. **Small map** — keep the root agent entry point short and use it as a map, not a manual.
2. **Hierarchical context / progressive disclosure** — load project-wide context first, then task-area context, then evidence only when needed.
3. **Scoped rules** — separate always-on rules from task-specific, on-demand, and audit/evidence rules.
4. **Promote repeated prose into machine enforcement** — when a rule can be checked reliably, prefer schema, test, linter, verifier, or code guard over repeatedly explaining it to the agent.

## Context tiers

### ALWAYS

Keep this layer minimal:

- project purpose / identity;
- authority order;
- absolute invariants;
- current-state pointer;
- where to look next.

A new session should normally begin here.

### TASK-SCOPED

Read only for the active work area, for example:

- one research project;
- one subsystem;
- one implementation package;
- one audit;
- one release or migration.

Put local rules near the files or workflow they govern instead of copying them into the root context.

### ON-DEMAND

Read only when a concrete question requires it:

- deep rationale;
- edge cases;
- recovery/debug procedures;
- old contradictions;
- detailed design alternatives;
- historical handoffs.

### EVIDENCE / ARCHIVE

Do not load by default:

- completed audit evidence;
- pressure-test logs;
- superseded designs;
- old execution transcripts;
- historical research batches;
- prior merge records.

These remain preserved for traceability, not as mandatory startup context.

## Documentation rules

- Do not turn `AGENTS.md`, `CLAUDE.md`, a Skill root file, or a handoff into a complete project encyclopedia.
- Prefer links to canonical documents over duplicated explanations.
- Separate **current truth** from **history/evidence**.
- Mark status and authority when ambiguity is possible: canonical, active, draft, evidence, historical, superseded.
- When a state/handoff file grows by accumulated history, move old history out and keep the current-state surface bounded.
- A task should not require reading unrelated project areas merely to discover the present state.
- Preserve long-form rationale and evidence, but keep it below the navigation layer.

## Machine-enforcement rule

When an important rule is repeated in prompts or documents and can be checked mechanically, consider moving enforcement into:

- JSON/schema contracts;
- type or state constraints;
- tests;
- linters;
- static verifiers;
- runtime guards;
- CI checks.

Keep prose for **why the rule exists, semantic distinctions, authority, and judgment boundaries**. Use machines for repeated compliance where practical.

Do not weaken semantics, provenance, safety, acceptance criteria, or auditability merely to save tokens.

## AI-facing tool / Skill rule

The same policy applies to tools:

- internal capability may stay rich;
- normal AI-facing surfaces should expose only what the common workflow needs;
- rare debug/audit operations should be discoverable or deferred rather than always visible;
- Skills should teach when/how/stop/recovery, not duplicate full tool schemas;
- measure the whole workflow cost: schemas + startup context + calls + retries + returned payloads.

## Session-start behavior

Unless a task explicitly requires deeper history:

1. read the small root map/instructions;
2. resolve the current authoritative state;
3. read only the active task's scoped documents;
4. descend into evidence/history only when a specific uncertainty, contradiction, or verification need appears.

If current truth cannot be identified without reading a large historical chain, treat that as a documentation-architecture problem and improve the navigation/authority layer rather than normalizing full-history rereads.

# SDD Corpus README

## 1. Purpose

This directory contains the **Specification-Driven Development (SDD) corpus** for the `dw-iot-gateway` project.

The `sdd/` directory is the authoritative engineering specification space for:
- project intent
- system boundary
- safety constraints
- requirements
- acceptance criteria
- validation and verification planning
- architecture decisions
- milestone narrowing documents
- review artifacts
- traceability support

This directory exists so the project is not driven only by informal discussions, issue titles, or implementation-first decisions.

---

## 2. Repository Entry Points and Their Roles

### `README.md`
Repository-level human-facing project presentation.

Its purpose is to provide:
- motivation
- high-level context
- public project overview
- hardware/software summary
- human-readable safety disclaimer

At the current project phase, `README.md` is a human-oriented document and may remain in Portuguese.

### `sdd/README.md`
This file.

Its purpose is to:
- define the role of the SDD corpus
- explain how to navigate the specification set
- define the recommended reading order
- distinguish current authoritative artifacts from planned artifacts

This file is a navigation and usage guide for the engineering specification corpus.

### `AGENTS.md`
`AGENTS.md` is a planned repository-level agent execution entry point.

It is **not** part of the active execution workflow during the current SDD-baseline construction phase.

Once created and approved, `AGENTS.md` will define:
- how coding agents must operate in this repository
- which documents must be read before implementation
- what agents are allowed and not allowed to do
- what evidence agents must provide for task completion

**Rule:** `AGENTS.md` governs agent execution behavior, but `sdd/` contains the detailed project specification that agents and humans must follow.

---

## 3. Current Project Phase

Current active milestone:
- **M0 — Development Workflow Baseline Established**

Current project condition:
- the SDD corpus is being created in ordered tasks
- foundational architecture and process rules are still being formalized
- implementation work is not yet authorized by this file alone
- coding agents are not enabled until the M0 SDD baseline is complete and approved

This means the repository is currently in a **specification-baseline construction phase**.

---

## 4. Execution Boundary

### 4.1 Current execution rule
During milestone M0:
- humans may create, review, and approve SDD artifacts
- implementation-facing specifications may be drafted and refined
- coding agents must not be used for implementation work yet

### 4.2 Agent enablement rule
Coding agents may be used only after:
- the **M0 SDD baseline** is complete
- the relevant SDD artifacts are approved
- `AGENTS.md` exists and is approved
- the project manager explicitly releases a bounded issue for execution

### 4.3 Authority rule
This file may reference planned repository artifacts, but only:
- existing artifacts
- approved artifacts
- explicitly released task context

are authoritative for execution.

---

## 5. Scope of the SDD Corpus

This corpus applies to the `dw-iot-gateway` project.

At the current baseline, the project intent is:
- create an external sidecar controller for the target dishwasher context
- preserve the original internal protection chain of the machine
- automate only the intended external manual-equivalent control points
- maintain clean architectural boundaries
- support AI-agent implementation through explicit, testable, and traceable specifications

This corpus does **not** replace:
- the repository `README.md`
- implementation code
- test evidence
- issue tracking
- design review records

Instead, it defines the engineering source of truth that those artifacts must follow.

---

## 6. Language Convention

The repository currently uses a split language policy:

- human-facing repository documentation may remain in Portuguese during the current project phase
- code and implementation-facing artifacts must be written in English
- agent-facing instructions must be written in English
- the full SDD corpus must be written in English

This rule exists to keep implementation artifacts and agent-consumed specifications consistent and unambiguous.

---

## 7. Recommended Reading Order

### 7.1 For humans new to the project
1. Repository `README.md`
2. `sdd/README.md`
3. `sdd/PROJECT_OVERVIEW.md`
4. `sdd/SYSTEM_CONTEXT_BOUNDARY.md`
5. `sdd/SAFETY_CONSTRAINTS.md`
6. `sdd/REQUIREMENTS.md`
7. `sdd/ACCEPTANCE_CRITERIA.md`
8. `sdd/VALIDATION_VERIFICATION_PLAN.md`
9. `sdd/TRACEABILITY_MATRIX.md`
10. Relevant files under `sdd/decisions/`
11. Relevant files under `sdd/milestones/`
12. Relevant files under `sdd/reviews/`

### 7.2 For coding agents
This reading order becomes active only after the M0 SDD baseline is complete and approved.

Planned reading order for coding agents:
1. Root `AGENTS.md`
2. `sdd/README.md`
3. Current milestone packet under `sdd/milestones/`
4. Assigned issue description and linked artifacts
5. `sdd/PROJECT_OVERVIEW.md`
6. `sdd/SYSTEM_CONTEXT_BOUNDARY.md`
7. `sdd/SAFETY_CONSTRAINTS.md`
8. `sdd/REQUIREMENTS.md`
9. `sdd/ACCEPTANCE_CRITERIA.md`
10. `sdd/VALIDATION_VERIFICATION_PLAN.md`
11. Relevant ADRs
12. Relevant review checklists

### 7.3 For reviewers
1. Assigned issue
2. Linked requirement IDs
3. Relevant milestone packet
4. Relevant architecture decisions
5. Relevant review checklist
6. Validation evidence
7. Traceability updates

---

## 8. Document Map

### 8.1 Core project specification

#### `PROJECT_OVERVIEW.md`
Defines:
- project purpose
- project goals
- intended value
- approved assumptions
- high-level scope framing

#### `SYSTEM_CONTEXT_BOUNDARY.md`
Defines:
- system boundary
- external actors
- controlled elements
- observed elements
- out-of-scope functions
- boundary between the add-on controller and the original machine

#### `SAFETY_CONSTRAINTS.md`
Defines:
- safety philosophy
- preserved original protections
- safe-state policy
- fault behavior constraints
- limits of intended guarantees

#### `REQUIREMENTS.md`
Defines:
- structured requirements
- stable requirement IDs
- requirement wording suitable for traceability and verification

#### `ACCEPTANCE_CRITERIA.md`
Defines:
- approval conditions for requirement fulfillment
- approval conditions for milestone outputs
- acceptance basis for review decisions

#### `VALIDATION_VERIFICATION_PLAN.md`
Defines:
- how requirements will be verified
- how system behavior will be validated
- what evidence must be produced
- how bench and integration validation are expected to evolve

#### `TRACEABILITY_MATRIX.md`
Defines and records:
- links between requirements and design artifacts
- links between requirements and implementation issues
- links between requirements and tests
- links between requirements and acceptance evidence

### 8.2 Decisions

#### `decisions/`
Contains:
- Architecture Decision Records (ADRs)
- other controlled design decisions, when explicitly adopted

### 8.3 Milestone narrowing documents

#### `milestones/`
Contains milestone-specific specification packets that narrow global project rules into milestone-ready implementation context.

### 8.4 Issue support artifacts

#### `issue-templates/`
Contains reusable templates for:
- specification tasks
- implementation tasks
- review-driven task creation

### 8.5 Review artifacts

#### `reviews/`
Contains:
- review checklists
- review procedures
- review support material

---

## 9. Status Convention

When practical, SDD documents should use one of the following status labels:

- `Draft`
- `Approved`
- `Superseded`

A document must not be treated as authoritative for implementation until it is reviewed and approved by the project manager.

---

## 10. Maintenance Rules

1. The SDD corpus is the engineering source of truth for implementation-facing project knowledge.
2. Behavior must be specified before it is implemented.
3. Requirements must be explicit, bounded, and testable.
4. If a change affects behavior, interfaces, constraints, architecture, or verification logic, the corresponding SDD artifacts must be updated.
5. Milestone-specific documents may narrow scope, but they must not silently conflict with approved higher-level specifications.
6. Unresolved ambiguity must be surfaced explicitly and resolved through specification; it must not be filled in silently by an implementation agent.
7. Traceability must be preserved from requirement to issue to implementation to verification evidence.
8. Planned repository artifacts may be referenced, but only approved and existing artifacts are authoritative.
9. This file is an index and navigation guide; it does not authorize implementation by itself.

---

## 11. Practical Usage Rule

Implementation work is allowed only when the project manager explicitly releases a bounded issue for execution under the approved repository workflow.

Implementation work must rely on:
- approved higher-level SDD documents
- the active milestone packet
- the assigned issue description
- the applicable review and validation criteria
- the approved agent-governance rules, when agent execution is enabled

---

## 12. Intent of This File

This file exists to make the SDD corpus readable in a stable, explicit order by:
- humans
- reviewers
- future coding agents

It is intentionally an index and corpus guide.

It is not:
- a replacement for the constitution
- a replacement for requirements
- a replacement for acceptance criteria
- a replacement for validation planning
- a replacement for `AGENTS.md`
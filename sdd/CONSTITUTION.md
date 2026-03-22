# Project Constitution

**Document ID:** CONST-001  
**Status:** Draft  
**Owner:** Project Manager  
**Scope:** `dw-iot-gateway` repository  
**Language:** English  
**Last Updated:** 2026-03-22

---

## 1. Purpose

This constitution defines the governing rules for the specification-driven development workflow of the `dw-iot-gateway` project.

It exists to ensure that:
- implementation follows approved specifications
- architecture remains intentional and maintainable
- traceability is preserved
- verification and validation are planned before implementation
- coding agents operate only within explicit and approved boundaries

This constitution is the highest-level repository governance document for implementation-facing work inside the SDD corpus.

---

## 2. Authority

This constitution governs:
- the SDD corpus
- implementation-facing documentation
- milestone packets
- issue preparation for implementation
- code review expectations
- coding-agent execution rules, once agent execution is enabled

If any lower-level artifact conflicts with this constitution, this constitution takes precedence until the project manager approves a revision.

---

## 3. Project Nature and Intent

The project is governed as:
- a demonstrator of technical viability
- a personal engineering laboratory for specification-driven development and agent-assisted software development
- a clean-architecture embedded software project with strong emphasis on traceability, testability, and controlled change

The project is **not** governed as:
- a certified safety product
- a production appliance controller
- a replacement for the dishwasher’s original internal protection chain

The firmware and specifications must respect this intended scope at all times.

---

## 4. Language Policy

The repository uses the following language convention:

- human-facing repository documentation may remain in Portuguese during the current project phase
- code and implementation-facing artifacts must be written in English
- agent-facing instructions must be written in English
- the full SDD corpus must be written in English

This rule exists to keep implementation artifacts and agent-consumed specifications consistent and unambiguous.

---

## 5. Specification-First Rule

No implementation behavior is authoritative unless it is grounded in approved specification artifacts.

The project follows these rules:
1. behavior must be specified before it is implemented
2. implementation must not invent missing requirements
3. ambiguity must be resolved in specifications, not silently in code
4. milestone packets may narrow context, but they must not silently override approved higher-level specifications

If a required behavior is missing from the specification set, implementation must stop and specification refinement must be requested from the project manager before execution continues.

---

## 6. M0 Gate for Agent Execution

Coding agents must not be used for implementation work until the **M0 SDD baseline** is complete and approved.

Agent execution becomes allowed only when all of the following are true:
- the M0 SDD baseline is complete and approved
- `AGENTS.md` exists and is approved
- the relevant milestone packet exists and is approved, when applicable
- the assigned issue is explicitly released by the project manager
- the assigned issue is bounded, testable, and traceable

Before this gate is satisfied, humans may create and review specifications, but coding agents must not perform implementation work.

---

## 7. Requirement Quality Rule

All implementation-facing requirements must be:
- explicit
- bounded
- testable
- unambiguous
- traceable
- reviewable

Requirements must be written so they can be:
- allocated to implementation tasks
- verified by defined methods
- reviewed for completeness and consistency

Requirements must not be expressed as vague intentions when implementation or verification depends on them.

---

## 8. Architecture Governance Rule

The project must maintain a clean architectural separation between:
- core application logic
- interface adapters
- hardware abstraction
- platform-specific implementation details

The following architectural rules are mandatory:
1. core logic must not depend directly on specific external interfaces such as Telegram
2. core logic must not depend directly on low-level GPIO implementation details
3. external interfaces must be implemented as adapters over stable internal ports
4. hardware changes at low level must be isolated behind approved abstraction boundaries
5. architecture changes that affect boundaries or dependency direction must be recorded as decisions

The architecture must support replacement of:
- remote interface adapters
- low-level hardware drivers
- diagnostics adapters

without redesign of the core logic, unless an approved decision explicitly states otherwise.

---

## 9. Traceability Rule

Every implementation-facing change must be traceable.

The minimum traceability chain is:
- requirement or approved governing artifact
- issue or task
- implementation change
- verification evidence
- review outcome

The project must preserve traceability across:
- requirements
- acceptance criteria
- architecture decisions
- milestone packets
- issues
- branches
- commits
- pull requests
- tests
- review evidence

No code change is complete if its purpose cannot be traced to an approved need.

---

## 10. Verification and Validation Rule

Verification and validation must be planned, not improvised.

The project must define, before implementation when practical:
- what will be verified
- how it will be verified
- what will be validated
- how validation evidence will be collected
- what acceptance evidence is required for closure

The project must distinguish:
- **verification**: demonstrating conformance to specified requirements
- **validation**: demonstrating that the implemented behavior satisfies intended operational use within the approved project scope

Tests are required, but tests alone are not sufficient without traceability to requirements or acceptance criteria.

When agent execution is enabled, the execution package must include a Markdown verification and validation handoff artifact suitable for review and possible re-execution by another agent or reviewer.

At minimum, this handoff artifact must identify:
- what was verified
- how it was verified
- what was validated
- how validation evidence was collected
- what test scope was covered
- known limitations, exclusions, or open risks in the test set

---

## 11. Issue Readiness Rule

An issue is not ready for implementation unless it is:
- within approved scope
- linked to the relevant specification context
- bounded enough to avoid unstated behavior
- testable
- reviewable
- traceable

The project manager is the release authority for implementation tasks.

Moving an issue to active execution means the project manager judges that the issue contains enough approved context to be implemented safely.

---

## 12. Agent Governance Rule

When agent execution is enabled, agents must:
- follow approved SDD artifacts
- follow `AGENTS.md`
- stay strictly within assigned issue scope
- avoid inventing behavior
- provide evidence required by the issue and review process
- provide a Markdown handoff artifact suitable for another agent or reviewer to evaluate implementation scope, verification quality, and assurance coverage

Agent-generated output must be rejected if it:
- introduces unstated behavior
- touches out-of-scope hardware or interfaces
- bypasses architecture constraints
- lacks traceability
- lacks required tests or evidence
- silently changes approved design intent

If an agent fails because the issue is ambiguous or incomplete, the issue must be improved before a new agent run is authorized.

Repeated retries against the same unclear issue are not the default workflow.

---

## 13. Review and Approval Rule

No implementation-facing artifact becomes authoritative until it is reviewed and approved by the project manager.

Reviews must evaluate:
- compliance with governing artifacts
- compliance with approved specifications
- architectural consistency
- correctness and clarity
- traceability completeness
- adequacy of verification evidence
- unresolved risks and assumptions

Draft artifacts may guide discussion, but only approved artifacts authorize execution.

When agent execution is enabled, the review package must include a Markdown review handoff artifact that allows the project manager or another reviewer to evaluate compliance with the review criteria above.

---

## 14. Change Control Rule

If a change affects any of the following SDD artifacts or concerns:
- behavior
- interfaces
- requirements
- architecture boundaries
- safety assumptions
- verification logic
- acceptance criteria
- issue execution rules

the corresponding SDD artifacts must be updated and submitted for review before the change is treated as approved project intent.

Changes must not be applied only in code when they modify approved project intent. Such changes must be surfaced explicitly to the project manager for SDD-corpus review.

When a change is architectural or policy-level, it must be recorded through the approved decision mechanism.

When agent execution is enabled, any change that affects SDD artifacts must include a Markdown change-impact handoff artifact for project manager or reviewer evaluation.

At minimum, this handoff artifact must identify:
- what changed
- why the change was needed
- which SDD artifacts were updated
- which dependent artifacts may require future review

---

## 15. Safety and Scope Rule

The project must preserve the intended separation between the sidecar controller and the machine’s original internal protections.

The project must not silently drift into:
- replacing the machine’s internal protection logic
- claiming guarantees outside approved project scope
- treating demonstrator assumptions as certified safety guarantees

Any change that increases control authority, safety exposure, or integration criticality must be explicitly reviewed in the SDD corpus before implementation.

---

## 16. Document Status Rule

When practical, SDD documents should carry one of these statuses:
- `Draft`
- `Approved`
- `Superseded`

Only approved artifacts are authoritative for implementation.

If implementation depends on a non-approved artifact, execution must stop and the project manager must be notified before work continues.

---

## 17. Amendment Rule

This constitution may be amended only by explicit review and approval from the project manager.

Any amendment must:
- identify what changed
- explain why the change is needed
- preserve consistency with the rest of the SDD corpus
- trigger updates to dependent artifacts where necessary
- identify the dependent artifacts, issues, or reviews that may require future reassessment because they relied on the previous version

---

## 18. Practical Interpretation Rule

If a reader is unsure how to apply this constitution, the safe interpretation is:
- do not assume missing requirements
- do not implement ambiguous behavior
- refine the specification before proceeding
- preserve traceability and reviewability

This rule applies to humans and agents equally.

---

## 19. Reference Basis

This constitution is informed by:
- the repository README and current project intent
- specification-driven development practices
- official agent instruction guidance for Codex workflows
- requirements-engineering guidance emphasizing clarity, verifiability, and traceability
- systems-engineering guidance distinguishing verification from validation

The detailed rules in this constitution are project-specific and intentionally stricter than a minimal prototype workflow because this repository is also a laboratory for evaluating SDD and agent-assisted development discipline.
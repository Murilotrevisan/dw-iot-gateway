# Project Overview

**Document ID:** POV-001  
**Status:** Draft  
**Owner:** Project Manager  
**Scope:** `dw-iot-gateway` repository  
**Language:** English  
**Last Updated:** 2026-03-22

---

## 1. Purpose

This document defines the high-level overview of the `dw-iot-gateway` project.

Its purpose is to describe:
- why the project exists
- what the project is intended to achieve
- what value it is expected to provide
- what scope framing has already been approved
- what assumptions are already accepted at project level

This document is intentionally high level.

It is not:
- a requirements specification
- an architecture specification
- a validation plan
- a safety analysis
- an implementation task list

Those concerns are handled by other SDD artifacts.

---

## 2. Project Summary

`dw-iot-gateway` is an external sidecar controller project for an electromechanical dishwasher context based on the Praxis LLP04 machine used as the project reference.

The project aims to modernize selected manual operations through an ESP32-C6-based control unit, while preserving the machine's original internal protection chain and avoiding unnecessary intrusion into the internal safety logic of the appliance.

The project is also a personal engineering laboratory intended to exercise:
- embedded software architecture
- ESP-IDF development
- clean architecture in embedded systems
- specification-driven development
- AI-agent-assisted development under controlled engineering workflow

---

## 3. Project Classification

This project is classified as:
- a demonstrator of technical viability
- a personal development and experimentation platform
- an embedded software architecture exercise
- an SDD and agent-assisted development evaluation environment

This project is not classified as:
- a certified appliance control product
- a commercial automation product
- a formal replacement for the dishwasher's original internal protection mechanisms
- a guarantee of appliance safety beyond the explicitly approved scope

---

## 4. Problem Statement

The reference dishwasher context requires manual interaction for key operating actions, including timer selection, temperature selection, and water handling steps.

This creates two relevant engineering opportunities:
1. improve operator convenience by automating selected manual-equivalent operations
2. build a realistic embedded development laboratory focused on software quality, architecture, traceability, and AI-agent execution discipline

The project therefore addresses both:
- a practical automation problem
- a process and architecture learning objective

---

## 5. Project Goals

The approved high-level goals of the project are:

1. Create an external control solution capable of automating approved manual-equivalent operations of the target dishwasher context.
2. Preserve the original internal protection chain of the machine as the primary protection mechanism.
3. Build the solution using ESP32-C6, ESP-IDF, and embedded-oriented C++.
4. Establish a clean architecture that isolates:
   - core logic
   - interface adapters
   - hardware abstraction
   - platform-specific implementation
5. Create an SDD corpus that allows implementation work to be driven from explicit, reviewable, and traceable specifications.
6. Evaluate the use of coding agents under controlled conditions, with strict review, traceability, and rejection criteria.
7. Maintain a development workflow that supports bench-first validation before real-machine integration.

---

## 6. Intended Value

The project is intended to create value in four dimensions.

### 6.1 Functional value
Reduce the need for repetitive manual interaction in the approved control scope of the reference dishwasher context.

### 6.2 Engineering value
Serve as a hands-on platform for practicing embedded software development with:
- ESP-IDF
- clean architecture
- hardware abstraction
- verification-oriented workflow

### 6.3 Process value
Serve as a real-world testbed for specification-driven development with milestone-based planning, issue traceability, and document-first execution control.

### 6.4 AI workflow value
Provide a controlled environment to evaluate how well coding agents can implement bounded tasks from explicit specifications and how much overhead is required to make that process reliable.

---

## 7. Approved Scope Framing

At the current project baseline, the approved project framing is:

- the system is an **external sidecar controller**
- the original machine remains responsible for its internal protection functions
- the project automates only approved external manual-equivalent actions
- the project uses network-capable embedded control for remote-assisted operation
- the project is intended to evolve incrementally through milestones

The currently approved controlled elements are:
- two solenoid valves for water in/out control
- relay-driven simulation of approved manual control points related to timer and temperature selection

The detailed system boundary is defined in `SYSTEM_CONTEXT_BOUNDARY.md`.

The detailed safety interpretation is defined in `SAFETY_CONSTRAINTS.md`.

---

## 8. Out-of-Scope Framing

At the current project baseline, the following are out of scope unless later approved through the SDD workflow:

- replacing the machine's internal thermistor, water level sensor, lid sensor, fuse, or equivalent internal protection elements
- redesigning the dishwasher's internal power/control architecture
- treating the project as a certified safety controller
- introducing unapproved control authority over internal machine protections
- implementing behavior that is not explicitly justified by approved requirements or milestone context

This overview document does not define all out-of-scope conditions exhaustively. It defines only the high-level framing.

---

## 9. Approved Project Constraints

The following project-level constraints are already approved:

- **MCU platform:** ESP32-C6
- **Framework:** ESP-IDF
- **Baseline version:** ESP-IDF v5.5.2
- **RTOS/runtime baseline:** ESP-IDF FreeRTOS
- **Implementation language:** embedded-oriented C++
- **Development style:** specification-driven development
- **Architecture style:** clean architecture with strict abstraction boundaries
- **Validation approach:** bench-first, test-oriented, before live machine integration
- **Agent workflow gate:** coding agents are not enabled for implementation until the M0 SDD baseline is complete and approved

More detailed technical constraints are defined in later SDD artifacts.

The project adopts ESP-IDF FreeRTOS as part of the platform baseline. Detailed concurrency, tasking, synchronization, and timing design are defined in later architecture and implementation-facing artifacts.

---

## 10. Approved Project Assumptions

The current approved project assumptions are:

1. The machine's original internal protection chain remains authoritative for internal protection behavior.
2. The sidecar controller must not silently expand its control responsibility beyond the approved scope.
3. Software faults should fail toward a safe output state within the approved control boundary.
4. Boot, reset, brownout, and watchdog recovery must bring outputs to a safe state and report reset information.
5. Wi-Fi loss must not necessarily interrupt current operation, but the system must preserve operational coherence and later reporting according to approved specifications.
6. Bench validation and staged integration are required before relying on the system in the real hardware context.
7. The project manager remains the release authority for implementation work.

These are project-level assumptions only. Detailed requirements and fault behaviors belong in later documents.

---

## 11. Stakeholders and Roles

### 11.1 Project Manager
Defines project direction, approves specifications, releases issues for execution, and performs or delegates technical review.

### 11.2 Human Developer / Architect
Defines architecture, specifications, review criteria, and implementation constraints.

### 11.3 Coding Agents
May implement bounded tasks only after the approved SDD gate is satisfied and only within explicitly released issue scope.

### 11.4 Operator
Uses the resulting system within the approved demonstrator context.

---

## 12. Success Perspective

At a high level, the project will be considered successful if it demonstrates all of the following:

- the approved manual-equivalent control scope can be automated externally
- the architecture remains modular and change-tolerant
- the SDD workflow remains usable and reviewable
- traceability is preserved from specification to implementation and validation
- bench validation supports safe staged progress toward integration
- coding-agent participation can be meaningfully evaluated under controlled constraints

Detailed acceptance criteria are defined elsewhere.

---

## 13. Relationship to Other SDD Documents

This document must be read together with:
- `sdd/README.md`
- `sdd/CONSTITUTION.md`

This document is elaborated by:
- `SYSTEM_CONTEXT_BOUNDARY.md`
- `SAFETY_CONSTRAINTS.md`
- `REQUIREMENTS.md`
- `ACCEPTANCE_CRITERIA.md`
- `VALIDATION_VERIFICATION_PLAN.md`
- milestone-specific packets
- architecture decisions recorded under `sdd/decisions/`

---

## 14. Practical Interpretation Rule

If a reader needs information that is more specific than this document provides, this document is not the correct place to infer it.

The correct action is to consult the more specific SDD artifact for that concern, or to refine the specification if the needed information does not yet exist.
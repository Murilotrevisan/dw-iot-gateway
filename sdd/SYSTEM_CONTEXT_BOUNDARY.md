# System Context and Boundary

**Document ID:** SCB-001  
**Status:** Draft  
**Owner:** Project Manager  
**Scope:** `dw-iot-gateway` repository  
**Language:** English  
**Last Updated:** 2026-03-22

---

## 1. Purpose

This document defines the system context and the system boundary for the `dw-iot-gateway` project.

Its purpose is to identify:
- the system of interest
- external actors and external systems
- controlled elements
- observed elements
- interfaces across the system boundary
- authority limits of the sidecar controller
- what is explicitly out of scope for the sidecar system

This document is a boundary-definition artifact.

It is not:
- a detailed requirements specification
- a low-level hardware design
- an implementation architecture document
- a full safety analysis
- a wiring procedure

Those concerns are handled by other SDD artifacts.

---

## 2. System of Interest

The system of interest is the **external sidecar controller** implemented by the `dw-iot-gateway` project.

At the current project baseline, the system of interest consists of:
- the ESP32-C6-based control unit
- the sidecar control electronics and interfaces
- the relay-driving function used to emulate approved manual control points
- the external water-control actuation function implemented through approved solenoid valves
- the firmware running on the sidecar controller
- the external communication path used for approved remote-assisted operation
- the development and diagnostic entry points needed for validation and maintenance

The system of interest is external to the original dishwasher internal control/protection structure.

---

## 3. Context Summary

The project context is an electromechanical dishwasher installation in which selected manual actions are being externalized into a sidecar controller.

At the current baseline, the sidecar controller is intended to:
- automate approved manual-equivalent control points
- control approved external water in/out actuation
- provide network-capable remote-assisted operation
- preserve the original internal protection chain of the machine

The original dishwasher remains a distinct external system relative to the sidecar controller, even though the sidecar interacts with selected control points.

---

## 4. External Actors and External Systems

### 4.1 Human operator
The human operator is external to the sidecar system.

The operator may:
- command the system through approved control interfaces
- review diagnostics and status information
- power, connect, inspect, or maintain the sidecar assembly within approved procedures
- continue using the original machine manually where the project design allows this

### 4.2 Original dishwasher
The original dishwasher is external to the sidecar system.

It provides:
- the physical washing machine process
- the internal electromechanical behavior
- the original internal protection chain
- the original internal components such as heater, pump, thermistor, lid sensor, water level sensor, fuse, and other built-in protections

These internal elements are not owned by the sidecar controller.

### 4.3 Electrical power source
The mains electrical supply is external to the sidecar system.

It powers the broader installation context and affects both the dishwasher and the sidecar system.

### 4.4 Water source and drain path
The water source and drain destination are external to the sidecar system.

The sidecar may command approved external actuation associated with water inlet and drainage, but the water infrastructure itself remains external.

### 4.5 Remote control client
A remote control client is external to the sidecar system.

It represents the user-facing control path used through approved networked interfaces.

At the current project direction, remote-assisted operation is part of the intended project evolution, but the detailed interface behavior is specified elsewhere.

### 4.6 Development and validation tools
Debuggers, terminals, flashing tools, test harnesses, and bench instrumentation are external to the sidecar system.

They interact with the system during development, validation, and maintenance, but they are not part of the deployed system of interest.

---

## 5. Controlled Elements Inside Approved Boundary

At the current baseline, the sidecar controller is approved to control the following elements:

### 5.1 Water inlet actuation
The sidecar may command the approved solenoid valve used for water inlet control.

### 5.2 Water outlet actuation
The sidecar may command the approved solenoid valve used for water outlet / drainage control.

### 5.3 Manual control emulation through relays
The sidecar may command relay channels that emulate approved manual control points of the dishwasher user controls.

At the current approved project understanding, this includes:
- timer-related manual-equivalent actuation
- temperature-selector-related manual-equivalent actuation

The sidecar controls these through relay-driven emulation of approved external/manual interfaces, not by replacing the internal protection logic of the dishwasher.

---

## 6. Observed Elements

At the current baseline, the sidecar system is approved to observe the following categories of information:

### 6.1 Internal sidecar/controller information
The sidecar may observe and report:
- its own firmware state
- its own reset cause
- its own diagnostics and faults
- its own communication status
- its own commanded outputs
- approved validation/test information produced by bench instrumentation or loopback strategies

### 6.2 External machine-related observation within approved scope
The sidecar may observe external machine-related states only when such observation is explicitly implemented and approved through later specifications.

This document does not assume ownership of the dishwasher's internal sensing chain.

### 6.3 Non-owned internal machine protections
The dishwasher's internal protective elements remain external to the sidecar system.

They may influence the real-world result of a commanded action, but they are not considered sidecar-owned observation channels unless a later approved specification explicitly defines a passive observation interface.

---

## 7. Explicitly Non-Controlled Elements

The following elements are explicitly outside the sidecar control authority at the current baseline:

- internal thermistor or equivalent overtemperature protection
- internal water level sensing/protection
- lid interlock / lid sensor
- internal fuse or equivalent protective cutoff devices
- internal power/control logic that belongs to the dishwasher
- internal heater control logic as an independently re-engineered subsystem
- internal pump control logic as an independently re-engineered subsystem
- any internal protection component whose ownership belongs to the original machine design

The sidecar may influence some machine behavior indirectly through approved manual-equivalent controls, but it does not own these internal protections.

---

## 8. Interface Boundary Definition

The system boundary is crossed only through approved interfaces.

At the current baseline, these interface categories are:

### 8.1 Power interface
Electrical supply and power-related connection points required for the sidecar system to operate.

### 8.2 Actuation interface
Electrical outputs from the sidecar to:
- relay-driving circuitry for manual-control emulation
- approved water-control solenoid actuation

### 8.3 Communication interface
Communication paths used for:
- remote-assisted operation
- diagnostics
- engineering validation and maintenance

### 8.4 Debug and validation interface
Interfaces used during development and validation, including:
- flashing/programming
- debugging
- terminal access
- bench test interaction
- approved loopback or instrumentation support

### 8.5 Mechanical and installation interface
The physical sidecar enclosure, wiring integration, and installation relationship with the dishwasher context.

Detailed wiring and implementation constraints are not defined here.

---

## 9. Authority Boundary

The sidecar controller has **limited external control authority**.

Its authority is limited to:
- commanding approved external/manual-equivalent actions
- commanding approved external water-control actuation
- reporting its own state and approved externalized status information
- participating in approved remote-assisted operation

Its authority does not include:
- redefining the dishwasher's internal protection logic
- assuming ownership of the internal safety chain
- claiming control authority over internal protections that remain native to the original machine
- silently expanding project scope beyond approved boundary definitions

Any proposed increase in control authority must be explicitly approved through the SDD workflow before implementation.

---

## 10. Manual Operation Boundary

The project is intended to preserve the possibility of manual use where the approved design allows it.

At the current baseline:
- the sidecar is intended to emulate approved manual control points
- the sidecar is not intended to erase the conceptual distinction between manual control and sidecar-driven control
- manual fallback assumptions, where available in the final implementation, must be handled in later detailed specifications

This document does not define the detailed fallback behavior. It defines only that manual-equivalent control emulation is part of the approved project direction.

---

## 11. Out-of-Scope Boundary

At the current baseline, the following are out of scope unless later approved through the SDD workflow:

- replacing the original internal protection chain
- redesigning the dishwasher's internal electromechanical architecture
- asserting that the sidecar system is a certified safety controller
- implementing direct ownership of internal machine protective logic
- adding control authority over unapproved hardware elements
- assuming observation or feedback signals that are not explicitly specified
- treating development/debug tools as part of deployed functional behavior

This list is not necessarily exhaustive. It defines the currently approved out-of-scope boundary at project level.

---

## 12. Boundary Assumptions

The current approved boundary assumptions are:

1. The sidecar system is external to the dishwasher internal protection architecture.
2. The sidecar system may emulate approved manual control points, but it does not become the owner of the original machine's internal protective logic.
3. Water-control actuation through approved external solenoid valves is within sidecar scope.
4. Bench-validation-only interfaces may exist without being part of the deployed product behavior.
5. Additional observations, sensors, or control paths must not be assumed without explicit later approval.

Detailed behavioral consequences of these assumptions are defined elsewhere.

---

## 13. Boundary-Related Open Items

The following topics are expected to be refined in later artifacts:
- detailed remote interface behavior
- detailed diagnostic interface behavior
- exact installed wiring/interface constraints
- exact observation model for any future passive sensing
- exact fallback/manual-operation handling in the final integrated design

These items are not undefined by accident; they are intentionally deferred to more specific SDD artifacts.

---

## 14. Relationship to Other SDD Documents

This document must be read together with:
- `sdd/README.md`
- `sdd/CONSTITUTION.md`
- `sdd/PROJECT_OVERVIEW.md`

This document is elaborated by:
- `sdd/SAFETY_CONSTRAINTS.md`
- `sdd/REQUIREMENTS.md`
- `sdd/ACCEPTANCE_CRITERIA.md`
- `sdd/VALIDATION_VERIFICATION_PLAN.md`
- later architecture decisions and milestone packets

---

## 15. Practical Interpretation Rule

If a reader needs a decision about whether a component, signal, control path, or responsibility belongs to the sidecar system, this document is the first boundary reference.

If this document does not resolve the question explicitly, the safe interpretation is:
- do not assume ownership
- do not assume control authority
- do not assume observation authority
- refine the specification before implementation
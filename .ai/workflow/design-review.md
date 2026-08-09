# Design Review Workflow


## Purpose


Evaluate architecture-impacting changes before implementation.


The goal:


- maintain long-term system evolution;
- prevent unnecessary complexity;
- preserve architectural consistency;
- make important decisions explicit.



---

# 1. When Design Review Is Required


Design review is required for changes involving:


## Architecture Changes


Examples:


- introducing new architectural patterns;
- changing system boundaries;
- splitting or merging modules;
- introducing new infrastructure components;
- changing core data flow.



---

## New Core Capability


Examples:


- new shared platform capability;
- new framework-level abstraction;
- new infrastructure layer;
- new cross-cutting service.



---

## Significant Technology Change


Examples:


- replacing major dependencies;
- introducing new runtime;
- changing persistence technology;
- changing communication mechanism.



---

## Data Model Changes


Examples:


- changing core entities;
- changing ownership of data;
- changing consistency model.



---

# 2. When Design Review Is NOT Required


Do not trigger design review for:


- simple bug fixes;
- small feature implementation;
- local refactoring;
- test improvements;
- documentation updates;
- code cleanup without behavior change.



---

# 3. Problem Definition


Before proposing a solution, describe the problem.


## Current Situation


What exists today?


## Problem


What limitation or requirement triggered this change?


## Impact


Who or what is affected?



---

# 4. Consider Existing Solutions


Before creating new capability:


Check:


- existing modules;
- existing utilities;
- existing infrastructure;
- existing patterns.


Answer:


Why can existing capability not solve this problem?



---

# 5. Evaluate Alternatives


At least consider:


## Option A


Description:


Advantages:


Disadvantages:



## Option B


Description:


Advantages:


Disadvantages:



## Recommended Solution


Chosen approach:


Reason:


---

# 6. Architecture Principles


The proposed solution should follow:


## Incremental Evolution


Prefer:

simple implementation
↓
stable module
↓
independent service
↓
distributed system


Avoid:


building the final architecture before the problem exists.



---

## Clear Responsibility


Each module should have:


- clear purpose;
- clear boundary;
- clear ownership.



Avoid:


"utility modules" that become uncontrolled dependencies.



---

## Reuse Proven Capability


Prefer:


extending existing capabilities.


Avoid:


creating duplicate systems.



---

## Small Team Friendly


Consider:


- maintenance cost;
- operational burden;
- debugging difficulty.


A solution that requires unnecessary operational complexity is usually not preferred.



---

# 7. Operational Impact


Evaluate:


## Reliability


- failure mode;
- degradation strategy;
- recovery approach.



## Observability


How will we know:


- it works;
- it fails;
- where the problem is?



## Maintenance


Who will maintain this after implementation?



---

# 8. AI-Specific Review


When AI proposes architecture:


Check:


## Is this required by the current problem?


Not:

"Could be useful in the future"



---

## Is complexity justified?


Evaluate:


- implementation complexity;
- operational complexity;
- learning cost;
- future maintenance cost.



---

## Does this create reusable capability?


Prefer solutions that become:

- reusable modules;
- stable infrastructure;
- shared capability.



---

# 9. Decision Record


If the decision is important:


Create:


docs/architecture/adr/


Record:


## Context


Why this decision was needed.


## Decision


What was chosen.


## Alternatives


What was rejected.


## Consequences


Expected benefits and costs.



---

# 10. Review Output


Provide:


Problem:
Current Situation:
Affected Components:
Options Considered:
Recommended Solution:
Why This Solution:
Risks:
Migration Plan:
Documentation Updates Required:
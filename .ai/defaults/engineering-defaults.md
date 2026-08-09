# Engineering Defaults

Version: 1.0


# 1. Core Engineering Philosophy


## Complexity Management


Prefer the simplest solution that solves the real problem.


Complexity is a long-term maintenance cost.


Do not introduce complexity for:

- hypothetical scale;
- future uncertainty;
- technical curiosity;
- demonstrating technical capability.


Every technical decision should consider:

- what problem it solves;
- what complexity it introduces;
- how it will be maintained.


Technology should solve problems.

Technology itself is not the goal.



---

## Evolutionary Architecture


Architecture should evolve gradually based on real requirements.


Prefer:


Simple implementation

↓

Clear module boundary

↓

Independent component

↓

Independent service

↓

Distributed system


Do not skip evolution stages without real requirements.


Evolution does not mean every system must become more complex.


Stop at the simplest architecture that satisfies current needs.



---

## Capability Accumulation


Software systems should accumulate reusable capabilities.


Avoid repeatedly rebuilding mature capabilities such as:


- authentication;
- authorization;
- workflow;
- observability;
- billing;
- asset management.


However:


Do not create abstractions before real usage patterns emerge.


Prefer:


Solve real problems first.

↓

Identify repeated patterns.

↓

Extract reusable capability.



---

## Human Understandability


Code is written for humans first, machines second.


Optimize for:


- readability;
- maintainability;
- clear intent;
- future modification.


Do not optimize only for:


- implementation speed;
- fewer lines of code;
- short-term convenience.



---

# 2. Complexity Management


Before introducing:


- new technology;
- new dependency;
- new abstraction;
- new architecture;


Answer:


## Problem

What real problem does this solve?


## Existing Solutions

Why are existing capabilities insufficient?


## Complexity Cost

What additional complexity does this introduce?


Consider:


- implementation complexity;
- operational complexity;
- learning cost;
- maintenance cost.


## Long-term Ownership

Who will maintain this capability in the future?



---

# 3. Architecture Evolution


Architecture decisions should be driven by:


- business requirements;
- team capability;
- operational requirements;
- reliability needs.


Not by:


- technology trends;
- hypothetical future scale;
- architectural fashion.



A good architecture should support:


- clear boundaries;
- independent evolution;
- controlled complexity;
- incremental improvement.



---

# 4. Component Design


A good component should have:


## Clear Responsibility


A component should have one clear purpose.


Avoid:


- unclear ownership;
- generic utility modules;
- components that accumulate unrelated responsibilities.



## Stable Interface


Components should communicate through clear interfaces.


Avoid:


- hidden dependencies;
- uncontrolled coupling;
- shared mutable state.



## Data Ownership


Components should define:


- responsibility boundary;
- data ownership;
- lifecycle ownership.



## Evolution Path


Components should have a possible evolution path:


- internal module;
- independent component;
- independent service.


But do not extract prematurely.



---

# 5. Engineering Ownership


Engineers are responsible for the complete lifecycle of the code they create.


Responsibility includes:


- implementation;
- testing;
- debugging;
- operation;
- maintenance.


Code ownership does not end after commit.


Engineers should understand:


- how the system runs;
- how failures happen;
- how problems are diagnosed.



---

# 6. Dependency Philosophy


Every dependency has a long-term cost.


Prefer fewer dependencies.


Before introducing a dependency, evaluate:


- maintenance status;
- community health;
- license;
- security;
- replacement difficulty;
- operational impact.


Prefer:


- mature;
- well-maintained;
- widely adopted;


dependencies.


Be cautious with:


- small utility dependencies;
- abandoned projects;
- unnecessary wrappers.



A dependency should justify its existence by providing significant value.



---

# 7. Runtime Standards


## Node.js


Default environment:


- fnm for Node.js version management;
- pnpm for package management.


Version policy:


Use the latest LTS version unless explicitly specified.


Historical compatibility is not required unless there is a clear business requirement.



---

## Python


Default environment:


- pyenv for Python version management;
- uv for package and dependency management;
- venv for isolated runtime environments when required.


Version policy:


Use the latest stable supported version unless explicitly specified.



---

# 8. Release Management


Use Semantic Versioning.


Version format:


MAJOR.MINOR.PATCH


Rules:


MAJOR:

Breaking changes.


MINOR:

Backward-compatible features.


PATCH:

Backward-compatible bug fixes.



Use Conventional Commits.


Commits should be:


- focused;
- meaningful;
- easy to understand.



---

# 9. Reliability


Systems should assume failure.


A reliable system is not one that never fails.


A reliable system is one that can continue providing value when failures happen.


Prefer:


- graceful degradation;
- failure isolation;
- explicit error handling;
- recoverable operations;
- controlled failure impact.



Observability helps detect problems.


Observability does not replace:


- good architecture;
- failure isolation;
- recovery design.



Consider:


- how failures happen;
- how failures are detected;
- how failures are recovered.



---

# 10. AI Era Engineering


AI reduces implementation cost.


AI does not reduce system complexity.


AI increases the importance of:


- architecture quality;
- documentation quality;
- domain understanding;
- reusable capabilities;
- engineering knowledge accumulation.



The goal of AI-assisted development is not producing more code.


The goal is:


Building better systems with accumulated engineering knowledge.



AI-generated code must follow the same standards as human-written code.


Code quality, maintainability, and system evolution remain primary goals.
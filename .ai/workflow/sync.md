# Session Sync Workflow


## Purpose


Synchronize project documentation and AI memory with the current codebase.


Use this workflow when:


- human modified code;
- AI modified code;
- external changes were merged;
- documentation may be outdated.


---

# 1. Analyze Changes


Review:


- git diff;
- recent commits;
- modified files.


Understand:


- What changed?
- Why changed?
- Which components are affected?


Do not update documentation before understanding the change.



---

# 2. Check Documentation Impact


Determine whether changes affect:


## Architecture


Examples:

- component boundaries;
- data flow;
- system design.


Action:


Update:

docs/architecture/



Consider:

ADR.



---

## Component Behavior


Examples:

- API changes;
- module responsibility changes;
- workflow changes.


Action:


Update:

docs/components/




---

## Development Process


Examples:

- new commands;
- environment changes;
- build process changes.


Action:


Update:
docs/development/




---

## Operations


Examples:

- deployment;
- monitoring;
- configuration.


Action:


Update:
docs/operations/



---

# 3. Update Memory


Update:
.ai/memory.md



Only add knowledge that:


- affects future development;
- is not obvious from code;
- prevents repeated mistakes;
- records important decisions.


Do not record:


- temporary debugging;
- simple implementation details;
- information already clear from code.



---

# 4. Check Knowledge Confidence


When adding memory:


Classify:


## Confirmed


Verified by:


- code;
- tests;
- explicit decision.



## Assumed


Needs future verification.



## Deprecated


No longer valid.



---

# 5. Remove Outdated Information


Check:


- obsolete architecture descriptions;
- outdated decisions;
- invalid conventions.


Do not keep contradictory knowledge.



---

# 6. Final Synchronization Report


Provide:

Code Changes:
Documentation Updated:
Memory Updated:
Potential Inconsistencies:
Remaining Questions:
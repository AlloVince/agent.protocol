# Session End Workflow


## Purpose


Synchronize the result of the current session and leave enough context for the next session.


Before ending a session, ensure:


- code state is clear;
- documentation is synchronized;
- important knowledge is preserved;
- unfinished work is recorded.


---

# 1. Review Session Changes


Review:


- files changed during this session;
- implementation result;
- current git status.


Summarize:


- What was changed?
- Why was it changed?
- What was the final result?



---

# 2. Verify Implementation


Check:


## Code


Confirm:


- implementation matches requirements;
- no unnecessary changes remain;
- code follows project conventions.



## Tests


Confirm:


- relevant tests were added or updated;
- existing tests pass;
- known failures are documented.



## Scope


Confirm:


- unrelated files were not modified;
- temporary files are removed.



---

# 3. Synchronize Documentation


Check whether changes affect:


## Architecture


Update if:


- component boundaries changed;
- data flow changed;
- new architectural patterns introduced.


Location:

docs/architecture/


---

## Components


Update if:


- component responsibility changed;
- public interfaces changed;
- important behavior changed.


Location:


docs/components/


---

## Development


Update if:


- new commands added;
- environment changed;
- development workflow changed.


Location:


docs/development/


---

## Operations


Update if:


- deployment changed;
- configuration changed;
- runtime behavior changed.


Location:


docs/operations/


---

# 4. Update Project Memory


Review:


.ai/memory.md


Update only when this session produced knowledge useful for future development.


Good candidates:


- important decisions;
- new conventions;
- discovered constraints;
- debugging solutions;
- common mistakes to avoid.



Do not add:


- temporary implementation details;
- obvious code behavior;
- information already clear from source code.



---

# 5. Record Remaining Work


If unfinished:


Update:


.ai/memory.md


or:


PROJECT_HISTORY.md


Include:


## Current Status


What has been completed.


## Remaining Tasks


What still needs to be done.


## Next Step


The recommended continuation point.



---

# 6. Check Consistency


Verify:


Code

↓

Documentation

↓

Memory


are consistent.


If conflicts exist:


Prefer:


1. Current code
2. Tests
3. Explicit decisions
4. Documentation
5. Memory assumptions



---

# 7. Prepare Next Session Context


Create a short summary:


Session Summary:
Completed:

Changed:

Important Decisions:

Known Issues:

Recommended Next Step:



---

# 8. Git Status


Before finishing:


Check:


- changed files;
- untracked files;
- generated files.


Do not commit unless requested.
# Session Start Workflow


## Purpose


This document defines the standard procedure before starting any development session.


The goal:

Make the AI agent understand the current project state and work as an experienced team member.



---

# 1. Load Project Entry Information


Always read:

AGENTS.md



Understand:


- project purpose;
- project boundaries;
- engineering rules;
- documentation structure;
- development workflow.



---

# 2. Load Project Memory


Read:

.ai/memory.md



Focus on:


- architecture knowledge;
- important decisions;
- known limitations;
- common mistakes;
- debugging knowledge;
- current development focus;
- AI collaboration notes.


Do not treat assumptions as confirmed facts.

Check:

Knowledge Confidence section.



---

# 3. Load AI Development Rules


Read:

.ai/defaults/engineering-defaults.md
.ai/defaults/ai-coding-defaults.md



Apply these rules during the session.



---

# 4. Understand Current Task


Before modifying anything, identify:


## Goal


What problem are we solving?


## Scope


Which components may be affected?


## Constraints


What should not be changed?


## Expected Result


How do we know the task is completed?



---

# 5. Load Relevant Documentation


Only load documentation related to the current task.


Examples:


Architecture change:

docs/architecture/



Component change:
docs/components/<component>/

Development environment:
docs/development/
Operations:
docs/operations/



Do not read unrelated documents.



---

# 6. Inspect Existing Code


Before implementation:


Understand:


- current implementation;
- existing patterns;
- related dependencies;
- test coverage.


Prefer understanding existing solutions before creating new ones.



---

# 7. Determine Change Type


Classify the task:


## Simple Change


Examples:

- small bug fix;
- documentation change;
- minor adjustment.


Proceed directly.



## Feature Change


Before coding:


Summarize:


- affected components;
- implementation approach;
- possible risks.



## Architecture Change


Before coding:


Read:

.ai/workflow/design-review.md



Consider:


- architecture documentation update;
- ADR creation.



---

# 8. Confirm Understanding


Before coding, provide a short summary:

Task:
Understanding:
Affected Areas:
Approach:
Potential Risks:


Wait for confirmation when:


- requirements are unclear;
- architecture impact exists;
- multiple solutions are possible.



---

# 9. Begin Implementation


After understanding is confirmed:


Follow:


- minimal change principle;
- existing project conventions;
- documented architecture decisions.


Do not modify unrelated areas.


# 10. Context Budget


Before loading documents:


Prefer:

1. Smallest relevant document set.

2. Component documentation before global documentation.

3. Source code only after understanding documents.


Avoid:

Loading entire repository.


If context grows too large:

Summarize existing understanding before continuing.

之后所有沟通使用中文
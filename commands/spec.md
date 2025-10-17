---
description: Create or refine project specification using spec-driven methodology
---

Create a detailed specification for this project using DinCoder's spec-driven workflow.

## Workflow

1. **Initialize** (if needed):
   - Check if `.dincoder/` exists
   - If not, run `specify_start` with project name

2. **Gather Requirements**:
   - What problem are we solving?
   - Who are the users?
   - What does success look like?
   - What are the constraints?
   - What's out of scope?

3. **Create Specification**:
   - Run `specify_describe` with comprehensive details:
     - **Goals**: Why we're building this (business value)
     - **Requirements**: What it must do (functional & non-functional)
     - **Acceptance Criteria**: Testable when/then statements
     - **Edge Cases**: Error scenarios, boundary conditions
     - **Out of Scope**: Explicitly state what we're NOT building

4. **Validate Quality**:
   - Run `spec_validate` to check:
     - ✅ All required sections present
     - ✅ Acceptance criteria are testable
     - ✅ No unresolved clarifications
     - ✅ No implementation details (HOW) leaking into spec (WHAT)

5. **Refine if Needed**:
   - Address validation issues with `spec_refine`
   - Resolve ambiguities with `clarify_resolve`
   - Iterate until validation passes

6. **Confirm Completion**:
   - Specification should be clear, complete, and unambiguous
   - Ready for planning phase

## Remember

- Specifications focus on **WHAT** to build, not **HOW**
- Every feature needs **testable acceptance criteria**
- Flag assumptions as **clarifications**
- Be specific about what's **out of scope**

Ask clarifying questions to fill gaps!

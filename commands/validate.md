---
description: Run quality checks on specification before implementation
---

Validate specification quality to ensure it's ready for the planning phase.

## Workflow

1. **Run Validation**:
   - Execute `spec_validate` with all checks

2. **Review Results**:
   - ✅ **Completeness**: All required sections present
     - Goals
     - Requirements
     - Acceptance Criteria
     - Edge Cases
   - ✅ **Acceptance Criteria**: Testable when/then statements
   - ✅ **Clarifications**: No unresolved `[NEEDS CLARIFICATION]` markers
   - ✅ **Implementation Leakage**: No HOW details in WHAT sections

3. **Check Clarifications**:
   - Run `clarify_list` to view all clarifications
   - Resolve pending items with `clarify_resolve`

4. **Fix Issues**:
   - For each validation failure:
     - Run `spec_refine` with specific section and changes
     - Document rationale
     - Re-validate

5. **Verify Alignment**:
   - Run `artifacts_analyze` for cross-check
   - Ensure spec is self-consistent

6. **Approval**:
   - If all checks pass:
     - ✅ Spec is ready for planning
     - Suggest running `/plan` next
   - If checks fail:
     - ❌ List specific issues
     - Guide through fixes

## Quality Gates

Validation prevents incomplete specs from reaching implementation.
Only specs that pass all checks should proceed to planning.

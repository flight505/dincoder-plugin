---
description: Generate technical implementation plan from specification
---

Generate a detailed implementation plan from the project specification.

## Workflow

1. **Verify Prerequisites**:
   - Check spec exists: `artifacts_read` with `artifactType: "spec"`
   - If missing, run `/spec` first
   - Verify spec is validated: `spec_validate`

2. **Gather Technical Context**:
   - Preferred technology stack
   - Architecture patterns (monolith, microservices, serverless)
   - Performance requirements
   - Security considerations
   - Deployment environment

3. **Generate Plan**:
   - Run `plan_create` with constraints:
     ```
     Technology stack: [stack preferences]
     Architecture: [architecture choice]
     Performance: [performance requirements]
     Security: [security requirements]
     ```

4. **Validate Alignment**:
   - Run `artifacts_analyze` to verify:
     - All spec requirements addressed
     - No missing features
     - Plan is technically feasible
     - Spec-plan consistency

5. **Review Structure**:
   - **Milestones**: Major implementation phases
   - **Technical Decisions**: Architecture choices with rationale
   - **Implementation Phases**: Ordered development steps
   - **Dependencies**: External services, libraries

6. **Next Steps**:
   - If plan looks good, suggest `/tasks` to generate actionable items
   - Log key decisions to `research.md` using `research_append`

## Focus

The plan focuses on **HOW** to build what the spec defines.

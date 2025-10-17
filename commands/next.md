---
description: Show next actionable tasks ready to start
---

Display the highest-priority, unblocked tasks that are ready to work on now.

## Workflow

1. **Filter for Next Tasks**:
   - Run `tasks_filter` with:
     - `preset: "next"`
     - `limit: 5`
     - `sortBy: "priority"`

2. **Display Each Task**:
   - **Task ID**: [e.g., T042]
   - **Description**: [one-liner]
   - **Metadata**:
     - Phase: [phase]
     - Type: [type]
     - Priority: [high/medium/low]
     - Effort: [hours]
   - **Why Ready**: No blocking dependencies

3. **Recommend Starting Point**:
   - Analyze priorities
   - Consider current phase
   - Suggest which task to start first

4. **Offer Details**:
   - Ask if user wants to dive deeper into any specific task
   - Show related tasks if helpful

## Use Cases

- Starting a coding session
- Deciding what to work on next
- Daily planning
- Context switching between tasks

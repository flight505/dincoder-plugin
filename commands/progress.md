---
description: View comprehensive project progress report with statistics and charts
---

Generate a detailed progress report with actionable insights.

## Workflow

1. **Overall Statistics**:
   - Run `tasks_stats` with:
     - `groupBy: "all"`
     - `includeCharts: true`
     - `showBlockers: true`

2. **Next Actions**:
   - Run `tasks_filter` with `preset: "next"`
   - Show top 5 unblocked tasks

3. **Current Work**:
   - Run `tasks_search` for in-progress tasks
   - Check if any are blocked

4. **Generate Report**:
   ```
   # Project Progress Report

   ## Overall Status
   - Completion: X% (Y/Z tasks)
   - Phase distribution: [breakdown]
   - Type distribution: [breakdown]

   [ASCII Progress Chart]

   ## Recent Accomplishments
   [Completed tasks from last session]

   ## Current Work
   [Tasks in progress]

   ## Next Actions (Unblocked)
   1. [Task ID]: [Description] (priority: X, effort: Y)
   2. ...

   ## Blockers & Dependencies
   [Tasks blocked by incomplete dependencies]

   ## Recommendations
   - Focus area: [suggestion]
   - Concerns: [potential issues]
   - Velocity: [on track / ahead / behind]
   ```

5. **Actionable Insights**:
   - Highlight bottlenecks
   - Suggest focus areas
   - Flag risks early

## Use Cases

- Daily standup preparation
- Sprint planning
- Stakeholder updates
- Personal progress tracking

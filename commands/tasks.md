---
description: Generate actionable task list from implementation plan
---

Break down the implementation plan into granular, actionable tasks.

## Workflow

1. **Verify Plan Exists**:
   - Run `artifacts_read` with `artifactType: "plan"`
   - If missing, run `/plan` first

2. **Generate Tasks**:
   - Run `tasks_generate` with scope guidance
   - Break down into 1-point tasks (completable in one session)
   - Add metadata to each task:
     - `phase`: setup | implementation | testing | polish
     - `type`: frontend | backend | devops | testing | docs
     - `depends`: Task dependencies (T001, T002)
     - `priority`: high | medium | low
     - `effort`: Estimated hours (1-8)

3. **Visualize Dependencies**:
   - Run `tasks_visualize` with format: "mermaid"
   - Review dependency graph for:
     - Circular dependencies (auto-detected)
     - Critical path
     - Parallelization opportunities

4. **Analyze Scope**:
   - Run `tasks_stats` with:
     - `groupBy: "all"`
     - `includeCharts: true`
   - Review:
     - Total tasks by phase/type
     - Estimated total effort
     - Blocker analysis

5. **Identify Next Actions**:
   - Run `tasks_filter` with `preset: "next"`
   - Show unblocked, high-priority tasks
   - Recommend starting point

6. **Begin Implementation**:
   - Start with first unblocked task
   - Mark complete with `tasks_tick` when done
   - Use `/progress` to track advancement

## Task Metadata Format

```
- [ ] Task description (phase: setup, type: backend, depends: T001, priority: high, effort: 3)
```

## Tips

- Keep tasks atomic (one clear deliverable)
- Use dependencies to enforce order
- Tag by type for filtering (frontend, backend, etc.)
- Update status regularly for accurate progress tracking

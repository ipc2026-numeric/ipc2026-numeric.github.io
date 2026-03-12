---
layout: default
title: International Planning Competition 2026 - Numeric Tracks
---

# International Planning Competition 2026 - Numeric Tracks

This is the website for the numeric tracks of the IPC 2026

## Calls
Please forward the following calls to all interested parties.

 - [Call for Domains](calls/ipc2026-call-for-domains.txt)


## Preliminary Schedule

| Event                                   | Date |
|:----------------------------------------|:-----|
| Domain submission deadline              | March 31, 2026 |
| Planner submission deadline             | May 10, 2026 |
| Planner abstract submission deadline    | June 10, 2026 |
| Contest run                             | May - June, 2026 |
| Results announced                       | June / July 2026 |

## Tracks


### Optimal Track
- single CPU core
- 8Gb memory limit
- 30min time limit
- Plans must be optimal
- The score of a planner is the number of solved tasks
- If a suboptimal or invalid plan is returned, all tasks in the domain are counted as unsolved
- If that happens in more than one domain, the entry is disqualified.

## Satisficing Track
- single CPU core
- 8Gb memory limit
- 30min time limit
- A planner may solve a task by producing multiple plans (e.g., in an anytime fashion). In such cases, only the plan with the lowest cost among those produced is considered
- The score of a planner on a task is C*/C, where C is the cost of the plan found by the planner and C* is the best known cost for that task. If the task is unsolved, the score is 0. The overall score of a planner is the sum of its scores across all tasks
- If an invalid plan is returned, all tasks in the domain are counted as unsolved
- If that happens in more than one domain, the entry is disqualified.

## Agile Track
- single CPU core
- 8Gb memory limit
- 5min time limit
- The cost of the discovered plan is ignored; only the CPU time required to find a plan is considered
- The score of a planner on a solved task is 1 if the task was solved within 1 second and 0 if the task was not solved within the resource limits. If the task was solved in T seconds (1 ≤ T ≤ 300), then its score is 1 - log(T)/log(300). The score of a planner is the sum of its scores for all tasks
- If an invalid plan is returned, all tasks in the domain are counted as unsolved
- If that happens in more than one domain, the entry is disqualified.

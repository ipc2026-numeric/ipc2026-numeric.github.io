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

## PDDL Fragment
Similarly to the Numeric IPC 2023 (https://ipc2023-numeric.github.io), we will use a subset of PDDL 2.1, considering two fragments:
- Simple Numeric Planning (SNP): Numeric variables can only be increased or decreased by a constant using the increase and decrease operations.
- Linear Numeric Planning (LNP): In addition to SNP, numeric variables can now be also assigned directly using the assign operator and the right-hand of an effect can now be a linear combination.

Preconditions and goals are arbitrary propositional formulas. That is, they include quantifiers, negative preconditions, disjunctive preconditions and any number of numeric predicates. Terms can either be literals as in classical planning, or numeric terms of the form f(X){ >=,>, =} 0 where f(X) is a linear expressions. Each domain of  the competition will be either a SNP or a LNP (LNP is more expressive than SNP).

Moreover, actions will have an associated state-independent non-negative cost, so optimal plans are those where the sum of action costs is minimal.


## Registration
We require that a planner is registered through a team. For this, you need to send an email with a subject containing “[Registration for Numeric Tracks]” to either f.percassi@hud.ac.uk or luigibonassi@robots.ox.ac.uk, and include the other address in CC. The email must contain:

names of participants, email contacts, track (agile/satisficing/optimal), and at least one GitHub account.
Based on that, we will create a private repository under the ipc2026-numeric organisation and grant all participants write access. Participants will be able to upload their planners and commit changes to the repository as needed until the planner submission deadline.

## Planner Submission
Competitors must submit the source code of their planners. The organisers will run the planners on the competition domains and problems, which will remain unknown to competitors until the evaluation phase. This prevents any fine-tuning of planners to the final benchmark set. Planner repositories will be hosted by the organisers on GitHub under the ipc2026-numeric organisation. These repositories will remain private until the end of the competition, after which they will be made public. Once the competition is concluded, we plan to make all planners, domains, and related data available from a single location.

We require participants to provide self-contained code, with scripts for compilation and running, “compile” and “run”, respectively. Each run script should specify which track the planner should be included in and the supported numeric fragment. Multiple configurations for the same track or fragments are allowed. An example of how to structure your repository and which scripts to include can be found here: https://github.com/ipc2026-numeric/baseline. Should there be any questions about the planner submission, feel free to contact any of the organisers.

Configurations for SNP will be evaluated only on SNP domains, while LNP configurations will be run on the entire benchmark set.

We are still investigating the execution environment for the experiments, including the possible adoption of a container platform such as Apptainer (formerly Singularity). In the meantime, participants may assume that planners must compile on a fresh installation of Ubuntu 20.04 / 22.04 LTS. Further details will be provided soon.
The planner must be executable through a script that takes exactly three input parameters, in the following order: the domain file, the problem file, and the name of the file where the last solution found will be saved. The output plan must follow the standard IPC solution format, consisting of a list of actions separated by a new line.


# Learning project rules

Recorded from the user's cumulative requests on September 19, 2026. These are project requirements; later requests add to them unless explicitly cancelled or replaced.

## Purpose and working agreement

1. Build practical capability in production data and AI engineering, starting from Oracle/PLSQL and financial-services experience with little hands-on Python/cloud experience.
2. Use one growing Financial Data Reliability and AI Investigation Platform, with synthetic data and useful working increments.
3. Prepare for relevant interviews through implementation, independent coding, debugging, design reasoning and honest evidence. Do not promise an offer or treat course completion as proficiency.
4. Keep the goal and ultimate outcome visible in README.md.
5. Treat every request as an addition to the task queue. Record it, retain earlier work and report what is implemented, published or still pending.
6. Maintain 30 sequential daily learning issues, reusing the original 10 for Days 1–10. Day numbers express learning order; respect the existing 15–20 hours/week and carry unfinished work forward.
7. The first 30 days target working, intermediate Python through useful project progress. Teach first, then guide practice, then ask for independent code. Day 1 starts with Python coaching and no coding prerequisite.
8. Continue advanced/master-level Python during the rest of the project, with independent practical gates. Explicitly teach binding/rebinding, local/global/nonlocal scope, mutation versus rebinding, default-argument timing and late binding in the first-month sequence.

## Required issue pattern

Use exactly these main sections:

```markdown
## Goal
Build <behavior> so <practical outcome>.

## Context
Explain the project reason and define unfamiliar terms.

## Task
Coach the concept, then implement one focused change in a named project location.
State the boundary and what belongs in a later increment.

## Acceptance Criteria
- Observable behavior and relevant edge case.
- Earlier behavior remains working.
- The project still runs/builds as applicable.

## Hint
Search for <general concept>. Notice <one or two useful ideas>.
```

- One main concept and one concrete implementation task per issue, with prerequisites in Context when needed. Day 1 is the explicit coaching exception: use explanation and prediction before code is assigned.
- Give an exact project location or component, understandable language and behavioral completion criteria.
- Introduce a relevant technology nuance without expanding the issue into several topics.
- Use searchable hints. Do not supply the full implementation, exact solution steps, long lectures or unexplained framework behavior.
- Avoid documentation-only and test-only tasks unless that issue is explicitly teaching documentation or testing.
- Do not require new tests, reports or docs on every beginner issue. Retain dedicated testing/documentation increments and milestone evidence.
- Progress from a runnable program and small boundaries to validation, configuration, errors, separation of responsibilities, storage, integrations, testing, deployment and operation.
- Keep existing issue numbers and completed evidence; do not silently replace work the learner has already completed.

## Depth, ETL and production

- Every adopted technology needs coverage of execution behavior, edge cases, failure modes, limitations, performance and alternatives. Use [TECHNOLOGY-DEPTH.md](TECHNOLOGY-DEPTH.md).
- ETL and ELT must be explicit implementation tracks: extraction, transformation, loading, incremental changes, modelling, quality, scheduling, lineage, performance and recovery. Use [ETL-AND-INTERVIEW-TRACK.md](ETL-AND-INTERVIEW-TRACK.md).
- The final system must be deployable to production, including repeatable artifacts/infrastructure, secure configuration, migrations, observability, rollback and tested restoration. Use [PRODUCTION-DEPLOYMENT.md](PRODUCTION-DEPLOYMENT.md).
- Keep deployability, approved production deployment and sustained operation as separate assessed outcomes. A lab is not real production ownership.
- Adopt advanced complexity when the project's requirements justify it. New tools must receive a depth row and a measurable learning task.

## Interview and market alignment

- Research recent employer-hosted openings in data engineering, ETL, data platforms and applied AI, initially Pune and selected India roles.
- Record verification date, posting date when available, role, location, job ID, direct source and required versus preferred requirements. Mark unavailable pages and contradictory details rather than guessing.
- Map every relevant requirement from the reviewed sample to an implementation exercise, interview exercise, existing evidence or explicit gap. A role-specific mandatory tool remains mandatory for that role even when it is not part of the default stack.
- Include coding, advanced SQL, ETL troubleshooting, Spark/cloud design, production incidents, communication and leadership practice. Use unfamiliar variations and independent mock interviews.
- Keep claimed project skills, professional experience, seniority and education constraints separate. Do not invent experience or scores.
- Review market alignment at planning checkpoints and before applications. This rule does not itself create a background automation, apply to jobs or authorize outreach.

## Publishing and verification

- Push authorized project updates on a feature branch and keep the pull request reviewable. Only @Prem-Tomar updates or merges master under the repository policy.
- Verify issue publication, local links, document consistency and relevant code behavior. Report actual checks, not anticipated results.
- Use planned, implementing, evidence-ready, reviewed and complete accurately. Preserve unresolved requirements in the tracker.

## Request ledger

| User request | Recorded implementation / current boundary |
|---|---|
| Start learning; create 10 issues | Initial issues created; evolved into the 30-day sequence |
| Apply the reusable learning-issue pattern | Existing 30 issues use the five sections above |
| Create issues for the next 30 days | Days 01–30 published as issues #1–#30; completion remains learner work |
| Add goal and ultimate outcome to README | README includes both and links the daily sequence |
| Push it | Documentation branch and PR #31 created; subsequent queued documentation updates continue there |
| Include nuances of each selected technology | Technology depth plan and milestone evidence requirements |
| Make the project deployable to production | Deployment design, release gates and separate readiness/operation states |
| Record all the rules | This document and root AGENTS.md |
| Optimize learning for interviews and include ETL | ETL/ELT implementation sequence, interview drills and readiness checks |
| Check recent openings and include relevant requirements | Dated employer sample and requirement-to-learning mapping; professional/tool-specific gaps retained |
| Make master-level Python explicit | Dedicated coaching-to-expert syllabus and independent stage gates |
| Start with Python coaching, not a code assignment | Day 1 is a taught session; every later issue has coaching before implementation |
| Working/intermediate Python in 30 days with project value | First-month local ETL deliverable and independent assessment; original pipeline tasks preserved as P01–P30 |
| Teach late binding and binding/global nuances | Dedicated binding/scope lab and Days 12, 13 and 23; applied assessment on Day 30 |
| Push the accumulated changes when done | Update the existing feature branch and PR after verification; master merge remains with the owner |

When adding a new request, update this ledger and any affected issue, roadmap or acceptance gate. A documentation update records the requirement; it does not complete the associated learning or software implementation.

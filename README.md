# Ralph Loop But Better

A structured, test-driven autonomous software development loop built around Codex.

This project is an attempt to turn AI coding agents from “one-shot code generators” into disciplined software workers that can plan, implement, test, repair, retry, and document progress without losing control of the codebase.

The idea is simple:

> Give the agent a task.  
> Let it work.  
> Test everything.  
> Repair small errors in the same context.  
> Retry bigger failures with fresh context.  
> Never let the agent own the plan.

---

## Why this exists

Most AI coding workflows break down when the task gets long.

The agent starts strong, then slowly loses context, forgets product intent, edits unrelated files, weakens tests, or declares victory before the system actually works.

Ralph Loop for Codex is designed around a different assumption:

> The agent should not be trusted to decide when it is done.  
> The loop should decide.

This project treats Codex as the implementation worker, while a Python controller manages:

- task selection
- dependency validation
- context preparation
- test execution
- failure classification
- inner repairs
- outer retries
- progress tracking
- PRD state updates
- file-change budgets
- protected paths

The goal is not to make the agent “smarter by vibes.”

The goal is to build a controlled execution system around it.

---

## Core concept

The system separates the project into several sources of truth:

```text
docs/project_description.md  → what the project is
PRD.json                     → what the agents must build
tasks/T{id}-{title}/          → what happened on each task
tests/                       → whether the work is actually done
Python controller             → who is allowed to update state

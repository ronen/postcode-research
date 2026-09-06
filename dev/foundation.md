# Application Development Foundation

This document describes foundational practices and agent guidance for the PostCode application repository. It can be used both to initialize the repository and to review whether its development foundation remains complete. Exact paths and wording may vary.

The application repository should provide equivalents of:

- [`task-protocol.md`](task-protocol.md), which defines its durable task lifecycle;
- [`conventions.md`](conventions.md), together with the `.gitignore` rules that implement its conventions;
- the operational development workflow, once defined.

## Suggested Elements for `AGENTS.md`

- **Session startup**

  ```markdown
  ## Session Startup

  Before performing substantive implementation work, read and follow [`dev/task-protocol.md`](dev/task-protocol.md).

  - If `_work/TASK.md` exists, begin that task according to the task protocol.
  - If the human asks to continue an existing task, locate and follow the relevant active task record.
  - Otherwise, work interactively. Do not create a task record until the human explicitly authorizes a substantive implementation request.
  ```

- **Development conventions**

  ```markdown
  ## Development Conventions

  Follow [`dev/conventions.md`](dev/conventions.md).
  ```

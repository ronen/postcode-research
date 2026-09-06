# Application Repository Setup

This document is for the human establishing or reviewing the PostCode application repository. It describes material to adopt into that repository. It is not itself an operative instruction for application-development agents.

## `README.md`

The repository's `README.md` should initially contain:

```markdown
# PostCode

PostCode is a software-development environment for humans understanding, directing, and supervising software built with coding agents, with the goal of enabling them to work at a conceptual level rather than through programming-language source code.

PostCode presents task-appropriate views of program structure, behavior, history, rationale, and other evidence. Projections preserve their provenance, epistemological status, and limitations so that derived facts, recorded assertions, observations, and interpretation are not presented as equally authoritative.

As an initial simplification, PostCode's projections and views are read-only. Humans continue to direct program changes by instructing coding agents in prose.

See [`foundation/product-design.md`](foundation/product-design.md) for the full conceptual design.
```

## `foundation/`

The repository should contain the following adopted foundation material:

```text
foundation/
  README.md
  product-design.md
  task-protocol.md
  baseline-conventions.md
```

The adopted documents should be copied verbatim from the following overview-project documents:

- `foundation/product-design.md` from [`../docs/product-design.md`](../docs/product-design.md);
- `foundation/task-protocol.md` from [`task-protocol.md`](task-protocol.md);
- `foundation/baseline-conventions.md` from [`baseline-conventions.md`](baseline-conventions.md).

`foundation/README.md` should contain:

```markdown
# Adopted Foundation

The documents in this directory are adopted foundation material for developing PostCode. Application-development agents should read and follow them where applicable, but must not modify them as part of ordinary development. The human may explicitly adopt revised versions.
```

## `AGENTS.md`

The repository's `AGENTS.md` should include the following elements:

- **Session startup**

  ```markdown
  ## Session Startup

  Before performing substantive implementation work, read and follow [`foundation/task-protocol.md`](foundation/task-protocol.md).

  - If `_work/TASK.md` exists, begin that task according to the task protocol.
  - If the human asks to continue an existing task, locate and follow the relevant active task record.
  - Otherwise, work interactively. Do not create a task record until the human explicitly authorizes a substantive implementation request.
  ```

- **Adopted foundation**

  ```markdown
  ## Adopted Foundation

  Read and follow the adopted documents under [`foundation/`](foundation/README.md) where applicable. Do not modify them as part of ordinary application development; the human may explicitly adopt revised versions.
  ```

- **Development conventions**

  ```markdown
  ## Development Conventions

  Follow [`foundation/baseline-conventions.md`](foundation/baseline-conventions.md) and any app-local conventions in `dev/conventions.md`.
  ```

## `.gitignore`

The root `.gitignore` should exclude `_work/TASK.md`, either through the explicit rule:

```gitignore
/_work/TASK.md
```

or through a broader rule that covers it.

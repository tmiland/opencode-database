# Memory Protocol

You have persistent memory across sessions, stored in the knowledge base at
`~/.opencode-database/` (the `memory` reference in your
config points at the same directory). Use it instead of asking
the user to repeat themselves.

## Read

- Before non-trivial work, skim `index.md`, then read only the files relevant
  to the current task.
- For project-specific context, look for
  `projects/<current-project-directory-name>.md`.

## Write

When you learn something durable — a user preference, environment fact, project
gotcha, decision with rationale, or a hard-won fix — record it right away:

- Preferences, environment, tooling, workflows → `user.md`
- General technical lessons → `learnings.md`
- Project-specific facts → `projects/<project-directory-name>.md`
  (missing? copy `projects/_TEMPLATE.md` and name the file exactly after the
  project directory)
- Created or renamed a file → update `index.md`

## Entry format

Append entries at the end of the file, newest last:

```
### YYYY-MM-DD — Short title
- Scope: <project-name | global>
- <Terse, concrete fact. 1–3 lines. Include exact commands/paths when relevant.>
```

## Rules

- Grep the target file first; update an existing entry rather than duplicating.
- The knowledge base is local-only: never commit, push, copy out, or otherwise
  share its contents.
- Never store secrets, transient task state, or anything already documented in
  the project's own README/AGENTS.md.
- Keep entries self-contained: a future session must understand them without
  this conversation's context.
- If an entry looks stale or wrong, fix or delete it instead of working around it.

# opencode-database

A persistent, centralized memory bank for opencode — every session, in any
project, can read and write it, so knowledge survives across conversations
without repeating yourself in every session.

Public-safe by design: this repo ships only the protocol and documentation.
The database itself is machine-local and lives outside any git repository,
so it can never be committed or published by accident.

## How it works

- The database lives at `~/.opencode-database/`: plain markdown notes — user
  preferences, general learnings, and one file per project under `projects/`.
- `INSTRUCTIONS.md` is the memory protocol. The global opencode config
  (`~/.config/opencode/opencode.jsonc`) loads it into every session via
  `instructions` and registers the database as the `memory` reference, so
  agents reach it from any project directory.
- No code, no dependencies: models use their normal file tools to read,
  grep, and append.

## Database layout

```
~/.opencode-database/
  index.md       table of contents (agents read this first)
  user.md        preferences, environment, workflows
  learnings.md   general technical lessons
  projects/      one file per project directory, created from _TEMPLATE.md
```

## This repository

`INSTRUCTIONS.md` (the protocol) is the only functional file; the rest is
documentation. Keep personal content out of this repo — the database never
lives here, and opencode session history is stored separately by opencode
itself.

If you move the database, update the `memory` reference path in
`~/.config/opencode/opencode.jsonc`, then restart opencode.

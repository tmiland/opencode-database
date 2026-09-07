# opencode-database

A persistent memory bank that every opencode session can read and write, so
knowledge survives across conversations and projects — without repeating
yourself in every session.

Public-safe by design: this repo ships only the protocol and skeleton. All
agent learnings stay local and are never committed (see `.gitignore`).

## How it works

- `knowledge/` holds plain markdown notes: user preferences, general
  learnings, and one file per project under `projects/`. Its contents are
  gitignored — they exist only on this machine.
- `INSTRUCTIONS.md` is the memory protocol. The global opencode config
  (`~/.config/opencode/opencode.jsonc`) loads it into every session via
  `instructions` and registers `knowledge/` as a `reference`, so agents can
  reach it from any project directory.
- No code, no dependencies: models use their normal file tools to read,
  grep, and append. Review local changes with plain file tools.

## Layout

```
knowledge/
  index.md               table of contents (agents read this first)
  user.md                preferences, environment, workflows   (local only)
  learnings.md           general technical lessons             (local only)
  projects/              one file per project directory        (local only)
  projects/_TEMPLATE.md  starting point for new project files
```

## Syncing across machines

The repo carries the protocol and skeleton only. To move your learnings to
another machine, copy `knowledge/` manually or push it to a separate private
repository — never to this one. If the bank lives at a different path on the
target machine, update the absolute path in
`~/.config/opencode/opencode.jsonc` (both `instructions` and `references`),
then restart opencode.

opencode session history is stored in `~/.local/share/opencode`, outside this
repository.

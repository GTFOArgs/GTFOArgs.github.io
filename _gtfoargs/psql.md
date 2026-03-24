---
title: psql
functions:
  command:
    - description: The `--output` argument pipes data through external commands when the value is prefixed with `|`.
      code: |
        psql -o'|id>/tmp/foo'
---

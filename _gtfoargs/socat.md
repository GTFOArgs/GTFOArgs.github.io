---
functions:
  file-read:
    - description: The command leverages socats ability to relay data, reading arbitary file by opening it in read-only mode.
      code: |
        socat -u OPEN:/etc/passwd,rdonly STDOUT
---

---
functions:
  file-read:
    - description: The command leverages socats ability to relay data, reading arbitary file by opening it in read-only mode.
      code: |
        socat -u OPEN:/etc/passwd,rdonly STDOUT
  shell:
    - description: The exec argument runs an arbitrary command and spawn a shell.
      code: |
        socat stdin exec:bash
  command:
    - description: The exec argument runs an arbitrary command.
      code: |
        socat stdin exec:whoami
---

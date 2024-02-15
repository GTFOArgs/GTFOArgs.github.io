---
description: LFTP is a file transfer client (FTP and other protocols).
functions:
  shell:
    - description: Stack commands that include launching a shell.
      code: |
        lftp -c '!bash'
  command:
    - description: Stack commands that include running a command.
      code: |
        lftp -c '!whoami'
  shell:
    - description: Stack commands that include launching a shell.
      code: |
        lftp -e '!bash'
  command:
    - description: Stack commands that include running a command.
      code: |
        lftp -e '!whoami'
  file-read:
    - description: Read an arbitrary file by specifying it as a script file.
      code: |
        lftp -f /etc/passwd
  file-write:
    - description: Overwrite a file, or create an empty file.
      code: |
        lftp -c 'mirror --script=lftp.script'
---

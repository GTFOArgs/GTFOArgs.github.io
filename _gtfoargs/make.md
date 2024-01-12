---
functions:
  shell:
    - description: Can be used to execute arbitrary commands on a system and spawn shells either indirectly
      code: |
        make -s --eval=$'x:\n\t-'"/bin/sh"
---

---
functions:
  file-read:
    - description: |
        Read an arbitrary file by specifying it as a magic file. This will
        result in errors containing the lines of the file. The argument parsing
        done by file also means this can be specified as a single argument.
      code: |
        file -m/etc/passwd
---

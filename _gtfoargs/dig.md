---
functions:
  file-read:
    - description: Read an arbitrary file by specifying it as a batch file. Note that this will leak lines of the file read as outbound DNS lookups.
      code: |
        dig -f /etc/passwd
---

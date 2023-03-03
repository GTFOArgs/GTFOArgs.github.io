---
description: When dealing with unzip, it may also be worth looking at the [zip-slip vulnerability](https://github.com/snyk/zip-slip-vulnerability).
functions:
  file-write:
    - description: Can be used to change the location the file is unzipped. In this example, the files are unzipped to /root/.
      code: |
        unzip -d /root/ archive.zip -d /tmp/
  file-read:
    - description: Can be used to read locate archives. The contents of the files and the filenames are shown.
      code: |
        unzip -c archive.zip
    - description: Can be used to read locate archives. The contents of the files are shown.
      code: |
        unzip -p archive.zip
---

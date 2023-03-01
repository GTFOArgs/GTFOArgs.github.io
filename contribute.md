---
layout: page
title: Contribute
---

## Structure

Each GTFO binary is defined in a file in the [`_gtfoargs/`] folder named as `<binary name>.md`, such file consists only of a [YAML] front matter which describes the binary and its functions.

The full syntax is the following:

```
---
description: Optional description of the binary
functions:
  FUNCTION:
    - description: Optional description of the example
      code: Code of the example
    - ....
  FUNCTION:
    - description: Optional description of the example
      code: Code of the example
    - ...
  ...
---
```

Where `FUNCTION` is one of the values described in the [`_data/functions.yml`] file.

Feel free to use any file in the [`_gtfoargs/`] folder as an example.

## Pull request process

Vendor software is accepted as well as standard Unix binaries. Binaries and techniques that only works on certain operating systems and versions are accepted and such limitations shall be noted in the `description` field.

Before sending a pull request of a new binary or function, ensure the following:

1. Verify the function works on at least one type of modern Unix system.
#2. ?

Pull requests adding new functions in [`_data/functions.yml`] are allowed and subjected to project maintainers vetting.

[YAML]: https://yaml.org/
[`_gtfoargs/`]: https://github.com/GTFOArgs/GTFOArgs.github.io/tree/master/_gtfoargs
[`_data/functions.yml`]: https://github.com/GTFOArgs/GTFOArgs.github.io/blob/master/_data/functions.yml

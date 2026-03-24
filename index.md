---
layout: page
title: "GTFOArgs: Argument Injection Exploitation Vector List"
---

![logo](/assets/logo.png){:.logo}

GTFOArgs is a curated list of Unix binaries that can be manipulated for argument injection, possibly resulting in security vulnerabilities.

Argument injection (sometimes referred to as parameter injection) takes advantage of a program's legitimate functionality in order to extend the capabilities provided by the method in which the program is intended to be run.

Argument injection is catalogued as [CAPEC-6][] by MITRE. It occurs when attacker-controlled input is passed as arguments to a program without proper sanitization — distinct from shell-metacharacter command injection. Common exploitation scenarios include injecting flags before an end-of-options delimiter (`--`), leveraging wildcard or glob expansion to turn filenames into options, and abusing legitimate program arguments that enable file operations or arbitrary command execution.

The project collects legitimate [arguments][] of Unix binaries that can be abused to break out of the environment they were run, in order to escalate privileges, transfer files, spawn bind and reverse shells, and facilitate other post-exploitation tasks.

GTFOArgs is a [collaborative][] project where everyone can [contribute][] with additional binaries and techniques. It is maintained by [Joshua Rogers][].

This project was inspired by [GTFOBins][] and most of the layout source code is written by them.


[arguments]: /arguments/
[GTFOBins]: https://gtfobins.github.io/
[collaborative]: https://github.com/GTFOArgs/GTFOArgs.github.io/graphs/contributors
[contribute]: /contribute/
[CAPEC-6]: https://capec.mitre.org/data/definitions/6.html
[Joshua Rogers]: https://joshua.hu/

{% include bin_table.html %}

---
layout: page
title: GTFOArgs
---

![logo](/assets/logo.png){:.logo}

GTFOArgs is a curated list of Unix binaries that can be manipulated for argument injection, possibly resulting in security vulnerabilities.

Argument injection (sometimes referred to as parameter injection) takes advantage of a program's legitimate functionality in order to extend the capabilities provided by the method in which the program is intended to be run.

The project collects legitimate [arguments](/arguments/) of Unix binaries that can be abused to break out of the environment they were run, in order to escalate privileges, transfer files, spawn bind and reverse shells, and facilitate other post-exploitation tasks.

GTFOArgs is a [collaborative][] project where everyone can [contribute][] with additional binaries and techniques.

This project was inspired by [GTFOBins][] and most of the layout source code is written by them.


[functions]: /functions/
[GTFOBins]: https://gtfobins.github.io/
[collaborative]: https://github.com/GTFOArgs/GTFOArgs.github.io/graphs/contributors
[contribute]: /contribute/

{% include bin_table.html %}

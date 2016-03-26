# Windows Task Scheduler schtasks.exe

(Based on [this](https://support.microsoft.com/en-us/kb/823093) question on support.microsoft.com) 

If the path of the scheduled task contains a whitespace, the whitespace must be escaped using backslash and double quotations **`\"`**

Problematic schtasks path won't work:

    schtasks /create /tn "my task" /tr "c:\foldername containing spaces\script.bat arguments" /sc once /sd 07/29/2003 /st 10:01

Corret path that works:

    schtasks /create /tn "my task" /tr "\"c:\foldername name containing spaces\script.bat\" arguments" /sc once /sd 07/29/2003 /st 10:01


References:
- MSDN Documentation: [schtasks.exe (Windows)](https://msdn.microsoft.com/en-us/library/windows/desktop/bb736357)
- SS64 Documentation: [schtasks](http://ss64.com/nt/schtasks.html)
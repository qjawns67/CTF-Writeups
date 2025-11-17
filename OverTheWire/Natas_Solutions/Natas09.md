## Username
natas9

## Password
ZE1ck82lmdGIoErlhQgWND6j2Wzz6b6t

## Write-Up
The logic of php code is that item that users submit is going to be a 'key' and server send grep result to us for dictionary.txt  
But a vulnerability of this code is passthru command.  
passthru() execute command that is all in the string, and show users that result.  
So attackers can use this command.  

Linux shell recognizes ';' for command separator, so next command of ';' could be executed too.  
We all know that all passwords are stored in /etc/natas_webpass.  
So if we submit ; cat /etc/natas_webpass/natas10, we can get a password for next level.  

## Method of solve
OS Command Injection from passthru() command

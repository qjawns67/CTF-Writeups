## Username
natas10

## Password
t7I5VHvpa14sJTUGV0cbEsbYfFP2dmOu

## Write-Up
For this level, logic of php code is the same as the previous level, but we can't use ';','|','&' separator.  
Unless we use these separator, we can still attack for OS Command Injection.  
In this situation, we have to utilize grep command effectively.  
grep command(e.g., grep -i A file_A file_B file_C) can be executed about multiple files.  
So if we submit any single alphabet(e.g., a) and then type /etc/natas_webpass/natas11, we can get password.  
 
## Method of solve
grep command injection

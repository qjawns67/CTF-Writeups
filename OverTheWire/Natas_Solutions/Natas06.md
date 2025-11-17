## Username
natas6

## Password
0RoJwHdSKWFTYR5WuiAewauSuNaBXned

## Write-Up
First of all, viewing source code, there is php code.  
The logic of php code is to give us password, if we POST right secret code.  
There is no evidence in the code, but there is a referenced file.  
When we check /includes/secret.inc, we can find out secret code, and then submit that code, we can get a password for next level.  

## Method of solve
Understanding php code

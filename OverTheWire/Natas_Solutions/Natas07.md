## Username
natas7

## Password
bmg8SvU1LizuWjx3y7xkNERkHxGre0GS

## Write-Up
There is a hint comment in index.php code that password for natas8 is in /etc/natas_webpass/natas8  
To enter to internal file, we should use Local File Inclusion.  
If we change page variables into file address that we want to connect, we can get password for next level.  

## Method of solve
Local File Inclusion(LFI)

## Username
natas14

## Password
z3UYcr4v4uBpeX8f7EZbMHlzK4UR2XtQ

## Write-Up
<img width="1111" height="345" alt="image" src="https://github.com/user-attachments/assets/9d28ff59-b7c5-4cdb-bcbc-922974bda034" />  

As we view the source code, we can notice php code using SQL system.  
We don't know the username and password.  
But using SQL Injection, we can destroy that login system.  
This web server collect request information like this, username="###" and password="%%%".  
We can insert text, " or 1=1 -- -, removing string status for ", making always TRUE state for or 1=1, and removing all text after comment for -- -.  
So we can input any text for password area, and then get a password easily.  

## Method of solve
SQL Injection for login bypass  
" or 1=1 -- -

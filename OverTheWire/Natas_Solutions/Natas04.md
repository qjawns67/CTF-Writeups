## Username
natas4

## Password
QryZXc2e0zahULdHrtHxzyYkj59kUxLQ

## Write-Up
Because we are visiting from "", so access disallowed.  
We should come from "http://natas5.~.org/".  
To do this method, we should know HTTP Referer Header.  
HTTP Referer Header indicates previous page address where we were before connecting current page, when we send HTTP request.  
To change HTTP Referer Header, we should use curl program that indicates information of web page.  

curl -v -H Referer:http://natas5.natas.labs.overthewire.org/ -u natas4:QryZXc2e0zahULdHrtHxzyYkj59kUxLQ http://natas4.natas.labs.overthewire.org/  

## Method of solve
Using curl command to change HTTP Referer Header

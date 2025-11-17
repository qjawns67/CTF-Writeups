## Username
natas12

## Password
yZdkjAYZRd3R7tq7T5kXMjMJlOIkzDeB

## Write-Up
<img width="648" height="597" alt="image" src="https://github.com/user-attachments/assets/3a617714-6658-4ba8-8950-a2699550d9a2" />

If we choose .jpeg image file, it is uploaded to web server for random string name.  
We should know about File Upload Vulnerability.  
File upload hacking is that attackers abuse the function for file upload of website.  
Attackers can cheat and upload unauthorized type file that can execute command of web server.  
In my case, i used Burp Suite.  
Just before uploading a image, turn on Proxy Intercept.  
<img width="655" height="50" alt="image" src="https://github.com/user-attachments/assets/d8747c8b-34c3-4d3c-9758-aeddd4d0350e" />

We can intercept the http request.  
<img width="1275" height="636" alt="image" src="https://github.com/user-attachments/assets/508f1587-ed48-43b7-b681-a2670d765ee0" />



Like this, if we remove image file code, insert simple php code, and change file type, we can get a password.  

## Method of solve
File Upload Vulnerability  
How to use Burp Suite Interceptor  
Making Web Shell(simple php script file)  

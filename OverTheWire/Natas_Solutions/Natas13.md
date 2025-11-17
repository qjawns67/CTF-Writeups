## Username
natas13

## Password
trbs5pCjCrkuSknBBKHhaBxq6Wm1j3LC

## Write-Up
This level is upgraded from previous level, added function that restrict file type for only jpeg.  
There are a lot of bypass methods of file upload attack.  
First, using extension filters, the gatekeeper checks only name tags.  
So, we can use methods like Double Extension(.php.jpg), Case Variation(.Php), etc.  
Second, the gatekeeper checks name tags and Content-Type.  
Third, Magic Byte Filters that we will use for this level.  
All files have unique starting bytes, and the gatekeeper checks the first few bytes, and then it just pass us.  

<img width="1269" height="301" alt="image" src="https://github.com/user-attachments/assets/e4e97421-186c-46c0-8ec1-7447386bf378" />  

We should intercept http request before uploading file.  

<img width="906" height="911" alt="image" src="https://github.com/user-attachments/assets/2e42f36b-55e4-44ee-84a7-7d15f3fb83f1" />  

<img width="905" height="630" alt="image" src="https://github.com/user-attachments/assets/9b0bbc07-8dcc-4845-8f32-18ff7bf47aca" />  

First of all, we should change the file extension from .jpeg to .php for viewing the result.  
And we should leave first four bytes for disguising file type, and then script php code like natas12.  

Then, we can get a password for next level.

## Method of solve
Using bypass methods when file upload attacking.

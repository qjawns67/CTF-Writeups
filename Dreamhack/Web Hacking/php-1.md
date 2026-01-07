## Description
<img width="1084" height="677" alt="image" src="https://github.com/user-attachments/assets/2cf906db-6f51-4bed-88a8-46a97643eba2" />

index.php: that shows other php pages for GET parameter

<img width="994" height="194" alt="image" src="https://github.com/user-attachments/assets/a53eaab4-7705-4ed8-a072-13fed1a33c40" />

list.php that shows uploaded file lists

<img width="476" height="216" alt="image" src="https://github.com/user-attachments/assets/5d4f5bd3-c25f-4fbb-b1e6-6891e9bd2386" />

view.php that print out for uploaded file.

There is limitation check for 'flag' word and ':'  
-> So we can't use stuff in this page
## Vulnerability
LFI(Local File Inversion)  
We should notice the page index.php where is no check for our parameter input.

## Exploit
So we should use PHP Wrapper in this index.php page.  
```
/?page=php://filter/convert.base64-encode/resource=../uploads/flag
```
index page add .php next to that payload, and print out flag.php.  
php://filter/ -> Wrapper Start  
convert.base64-encode -> Filtering type  
resource= -> target path  

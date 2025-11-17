## Username
natas11

## Password
UJdqkK1pTu6VLt9UHWAgRZz6sVUZ3lEk

## Write-Up

```php
<?php
// Finding Key Process
// A^Key=B -> A^B=Key
$cookie='HmYkBwozJw4WNyAAFyB1VUcqOE1JZjUIBis7ABdmbU1GIjEJAyIxTRg%3D';
function xor_encrypt($in) {
    $default_data = '{"showpassword":"no","bgcolor":"#ffffff"}';
    $text = $in;
    $outText = '';

    // Iterate through each character
    for($i=0;$i<strlen($text);$i++) {
    $outText .= $text[$i] ^ $default_data[$i];
    }

    return $outText;
}
//Decoding Base64
$decoded_base64=base64_decode($cookie);
print(xor_encrypt($decoded_base64));
?>
```

##### Output

    eDWoeDWoeDWoeDWoeDWoeDWoeDWoeDWoeDWoeDWoe
    
We got a key.  
Now we have to make a new cookie.

```php
<?php
//New data that showpassword is yes for right cookie
$new_data=array("showpassword"=>"yes", "bgcolor"=>"#ffffff");
function xor_encrypt($in) {
    $key = 'eDWo';
    $text = $in;
    $outText = '';

    // Iterate through each character
    for($i=0;$i<strlen($text);$i++) {
    $outText .= $text[$i] ^ $key[$i % strlen($key)];
    }

    return $outText;
}
$encoded_json=json_encode($new_data);
$encrypted_xor=xor_encrypt($encoded_json);
$encoded_base64=base64_encode($encrypted_xor);

print($encoded_base64);
?>
```


## Method of solve
XOR Encryption  
Scripting PHP code

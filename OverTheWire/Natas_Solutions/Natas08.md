## Username
natas8

## Password
xcoXLmzMkoIP9D7hlgPlh9XD7OgLAe5Q

## Write-Up
we have to find out decoded Secret code.  
encodedSecret is submit_code -> base64 encode -> reverse -> binary-to-hex.  
So we have to decode this secret in sequence hex-to-binary -> reverse -> base64 decode.  
We can solve this problem if we can control each linux command.  

hex-to-bin: xxd -r -p  
reverse: rev  
base64 decoding: base64 -d  

## Method of solve
Encoding and Decoding

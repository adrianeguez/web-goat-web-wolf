# WebGoat

## Instalacion

WebGoat

```
$ docker run -p 8080:8080 -it -v /tmp/webgoat-data-8-0:/home/webgoat/.webgoat
-v8.0.0.M14 webgoat/webgoat-8.0 /home/webgoat/start.sh
```

Conocer la ip del contenedor de webgoat. En este caso es `172.17.0.2`.

```
$ docker ps -a
...
...
"Networks": {
                "bridge": {
                    "IPAMConfig": null,
                    "Links": null,
                    "Aliases": null,
                    "NetworkID": "88024ddd37d9194ca0a5f0976280f09e73077d778f8cce7559e694de3a611c18",
                    "EndpointID": "4d6988ee90aa2421a139ec8d46762c63a0dfdf283c5eac49432048b666ad092c",
                    "Gateway": "172.17.0.1",
                    "IPAddress": "172.17.0.2",
                    "IPPrefixLen": 16,
                    "IPv6Gateway": "",
                    "GlobalIPv6Address": "",
                    "GlobalIPv6PrefixLen": 0,
                    "MacAddress": "02:42:ac:11:00:02",
                    "DriverOpts": null
                }
            }

...
...
```


Para instalar WebWolf debemos de usar la direccion ip de antes, en este caso esta como una variable de entorno `webgoat.server.address` con el valor `172.17.0.2` que encontramos con el anterior comando.

```
$ docker run -p 8080:8080 -it -v /tmp/webgoat-data-8-0:/home/webgoat/.webgoat
-v8.0.0.M14 webgoat/webgoat-8.0 -e webgoat.server.address=172.17.0.2 /home/webgoat/start.sh
```

Para empezar crear una cuenta en [(http://localhost:8080/WebGoat](http://localhost:8080/WebGoat) y luego iniciar sesion en WebWolf [(http://localhost:9090/login](http://localhost:9090/login)
# WebGoat

## Instalacion

WebGoat

```
$ docker run -p 8080:8080 -it -v /tmp/webgoat-data-8-0:/home/webgoat/.webgoat -v8.0.0.M14 webgoat/webgoat-8.0 /home/webgoat/start.sh
```

Conocer la ip del contenedor de webgoat. En este caso es `172.17.0.2`.

```
$ docker ps -a

CONTAINER ID        IMAGE                      COMMAND                  CREATED             STATUS                      PORTS                     NAMES
f491e6aa2809        webgoat/webgoat-8.0        "java -Djava.securit…"   12 seconds ago      Up 11 seconds               0.0.0.0:8080->8080/tcp    cocky_proskuriakova
eb5f455290e3        mariadb:latest             "docker-entrypoint.s…"   4 weeks ago         Exited (255) 4 weeks ago    0.0.0.0:3307->3306/tcp    mariadb
13ef50e1141e        bitnami/tomcat:8.5.31      "/app-entrypoint.sh …"   6 weeks ago         Exited (255) 6 weeks ago    0.0.0.0:32773->8080/tcp   tomcat-4
aa9410d34e17        tomcat:8.5.31              "catalina.sh run"        6 weeks ago         Exited (130) 6 weeks ago                              tomcat-3
bc6f5d2c533a        mysql:latest               "docker-entrypoint.s…"   8 weeks ago         Exited (255) 7 weeks ago    0.0.0.0:32771->3306/tcp   mysql-facturacion
54aa59dda6b9        cloudesire/tomcat:8-jre8   "/run.sh"                5 months ago        Exited (255) 5 months ago   0.0.0.0:8080->8080/tcp    compassionate_austin
82b7de38a04a        cloudesire/tomcat:8-jre8   "/run.sh"                5 months ago        Created                                               vigilant_nightingale
19609e102670        tomcat:latest              "catalina.sh run"        5 months ago        Exited (255) 5 months ago   0.0.0.0:32774->8080/tcp   tomcat
9e959defc719        f008d8ff927d               "docker-entrypoint.s…"   5 months ago        Exited (255) 4 weeks ago    0.0.0.0:3306->3306/tcp    mysql
```

Luego usamos el identificador de nuestro contenedor en este caso `f491e6aa2809` para inspeccionar el contenedor:
```
$ docker inspect f49a
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
$ docker run -e webgoat.server.address=172.17.0.2 -it -p 9090:9090 webgoat/webwolf /home/webwolf/run.sh
```

Para empezar crear una cuenta en [(http://localhost:8080/WebGoat](http://localhost:8080/WebGoat) y luego iniciar sesion en WebWolf [(http://localhost:9090/login](http://localhost:9090/login)

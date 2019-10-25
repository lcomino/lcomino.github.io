---
layout: post
published: true
title: Build Android via wi-fi
date: '2019-10-25'
---
## Conectar no Android via TCPIP

Para conectar no seu aparelho via Wifi utilize os comandos abaixo

Alterando o modo de deploy do ADB para TCPIP e não mais USB `adb tcpip [PORT]`
```
$ adb tcpip 5555 
```

Depois para conectar utilize o comando `adb connect [IP_DO_APARELHO]:[PORT]` ficaria assim:

```
$ adb connect 192.168.1.xx:5555
```

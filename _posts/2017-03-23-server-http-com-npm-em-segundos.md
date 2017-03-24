---
layout: post
published: true
title: 'Server HTTP com NPM em segundos :)'
subtitle: Utilize npm http-server para rodar um server http em segundos
date: '2017-03-23'
---

Neste post vou mostrar uma dica marota que me mostraram hoje (Vlw Robson), de como rodar aquele 'serverzinho' http para seu projeto, de maneira simples e fácil utilizando [Node.js®](https://nodejs.org).

Primeiro deve ser instalado o `http-server` utilizando o comando `npm install http-server -g`.

Lembrando que você precisa ter o [Node.js®](https://nodejs.org) instalado já ;)

Feito isto, navegue até a pasta do seu projeto e digite o seguinte comando no terminal `http-server -c-1`. Este comando inicia o serviço na porta 8080 e o comando -c-1 desabilita o cache da parada.

Pronto, seu server http já estará rodando na porta 8080 e poderá ser acessado em [http://localhost:8080](http://localhost:8080).

```
	Starting up http-server, serving ./
	Available on:
  		http://10.1.1.13:8080
  		http://127.0.0.1:8080
	Hit CTRL-C to stop the server
```


Bom é isto, espero ter ajudado alguem ai, se ajudei, compartilhe o post ai com a galera e flws!

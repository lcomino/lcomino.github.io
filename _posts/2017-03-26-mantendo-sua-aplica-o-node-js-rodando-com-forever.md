---
layout: post
published: false
title: Mantendo sua aplicação node.js rodando com Forever
date: '2015-09-03'
---
Neste post iremos aprender de forma simples como deixar sua aplicação node.js rodando no background com o Forever.

Primeiro, precisamos instalar o Forever de maneira global via npm.

 `$ [sudo] npm install forever -g`

Agora é simples, é do acessar a pasta da sua aplicação e rodar o seguinte comando.

`forever start app.js`

Pronto, agora sua aplicação está rodando em background.

Lógico que esta é uma maneira simples e rápida de colocar seu app node.js no ar, existem muito mais configurações, que podem ser encontradas no repositório do [Forever no GitHub](https://github.com/foreverjs/forever).

Valeu, falou e thau!

![]({{site.baseurl}}/https://media.giphy.com/media/Fs09dnTdaW6D6/giphy.gif)


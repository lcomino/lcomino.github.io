---
layout: post
published: false
title: Monitorando as alterações do seu app Nodejs
date: '2015-09-02'
---
Você está fazendo aquela sua aplicação linda com Node.js, mas a cada alteração no seu app você precisa parar e iniciar sua aplicação no terminal. No começo pode até ser de boa, mas depois de um tempo fica meio chato fazer isto toda hora, ai que entra o nodemon!

Com ele, todas as alterações da sua aplicação serão atualizadas automaticamente.

Instalando

`$ npm install -g nodemon`

Talvez seja necessário usar o sudo :)
![](/content/images/2015/09/11990583_1491300521168402_2814846549246519085_n.jpg)

Depois de instalado é muito simples, para rodar sua aplicação no terminal não use mais

`$ node suaaplicacao.js `

Use agora o nodemon

`$ nodemon suaaplicacao.js`

Assim todas as alterações realizadas na sua aplicação serão recarregadas automaticamente.

Espero que ajude!
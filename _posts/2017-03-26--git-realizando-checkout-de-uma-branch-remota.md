---
layout: post
published: true
title: '#git - Realizando checkout de uma branch remota'
date: '2015-09-01'
---
Estou eu aqui aprendendo um pouco de git por vez.

Hoje criei um branch local e precisei enviar ela ao meu ‘server’ e venho aqui agora mostrar como eu fiz.

Primeiro envie sua branch para o remote:

$ git push -u origin nome_da_sua_nova_branch

Depois no seu servidor faça o seguinte:

$ git checkout -b origin/nome_da_sua_nova_branch

O mesmo vale para o contrário, caso sua branch nova esteja no servidor é só executar o comando.

Simples!

Esperam que tenham gostado, qualquer coisa só avisar.
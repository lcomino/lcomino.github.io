---
layout: post
published: false
title: Adicionando usuário no MySQL
date: '2015-10-22'
---
E ae blz?

Então, assunto não é muito novo mas creio que pode ajudar um pessoal ai, e esta é a intenção deste blog ;)

Bom, primeiro iremos acessar nosso MySQL pela linha de comando, se você ainda tem medo dela comece a perder este medo em.. ela não morde não rsrs é bem de boa.

Voltando.. acessar o MySQL.

`$ mysql -u root -p`

Tecle ENTER e digite a senha que foi criada na instalação.

Pronto você acessou o MySQL.

Agora vamos à criação do usuário em si. Digite o seguinte

`CREATE USER 'lcomino'@'localhost' identified by 'senhafodapracaralho';`

Simples correto? File!

Bom explicando, estamos criando um usuário lcomino com a senha (senhafodapracaralho).

Mas e ae, tentei acessar o MySQL com este usuário e não consegui por quê?

Calma, quando você cria um usuário ele vem sem permissão nenhuma, em banco nenhum.

Agora iremos dar estas permissões para ele.

`GRANT ALL ON *.* TO 'lcomino'@'localhost';`

Simples, liberamos tudo para este usuário, ele poderá acessar qualquer banco, qualquer tabela, qualquer procedure... etc, etc..

Isto não é ruim? Bom para um ambiente de produção sim.. :( mas localmente para desenvolvimento e aprendizado ta de boa :D

Bom agora só para garantir.. execute o comando:

`FLUSH PRIVILEGES`

Este comando ira recarregar os privilégios das 'grant tables' do MySQL.

Bom é isto ae, espero que tenha ajudado alguém e falou, valeu e até mais!

O que pode acontecer rsrs mas da nada não, normal.

![](http://i2.wp.com/memecollection.net/wp-content/uploads/2013/05/As-a-programmer.jpg?w=500) 

A ia me esquecendo.. puts que merda..

Seguinte, e se eu quiser remover o usuario?

Simples...

`DROP 'lcomino'@'localhost';`

E depois...

`FLUSH PRIVILEGES;`

E o usuário já era!!

Agora sim, fui!
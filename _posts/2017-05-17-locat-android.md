---
layout: post
published: true
title: Utilizando o ADB do Android SDK para visualizar o log do seu device Android.
date: '2017-05-17'
---

Sabe quando você precisa simplesmente analisar aquele erro que está ocorrendo no seu APP
mas não quer abrir o Android Studio para visualizar o log do aparelho. Então vamos ver como 
fazer isto utilizando uma ferramenta da SDK do Android, o ADB.  

---  

# Requisitos

* Android SDK instalado
* Path para a pasta platform-tools configurado
* Um device Android (óbvio) com Opções de Desenvolvedor Ativas e Depuração USB também ativa. ;)

# Começando

Conecte seu device via USB no seu computador, feito isto vamos verificar se ele está corretamente conectado utilizando o comando `adb devices`

O retorno será algo parecido com isto

```
$ adb devices
List of devices attached
0123456789ABCDEF        device

```

Se ele aparecer na lista agora podemos utilizar o comando do logcat em si.

Ainda no terminal, execute o comando `adb shell logcat`

No terminal agora irá aparecer todo o log do seu aparelho conectado, algo como abaixo:

[gif aqui]

Mas, isto não ajuda muito certo?Não, então vamos gravar ele em um txt para ver se melhora a situação?

Execute o comando novamente, mas agora jogando o retorno em um arquivo TXT.

```
$ adb shell logcat > log.txt

```

Agora fica mais fácil buscar algo no log, mas ainda é complicado, vamos melhorar mais um pouco?

Vamos filtrar somente o que precisamos do resultado, por exemplo, a aplicação que estou analisando possui um comando que envia para o log uma string específica com o ERRO, por exemplo ERRO_APLICACAO_X.

Vamos filtrar o texto e exibir somente oque apresenta a palabra ERRO_APLICACAO_X.

Terminal

```
$ adb shell logcat | grep ERRO_APLICACAO_X
```

Prompt Windows (CMD):

```
$ adb shell logcat | findstr /R /C:"ERRO_APLICACAO_X"

```

PowerShell:


```
adb shell logcat | select-string -pattern 'ERRO_APLICACAO_X'

```

Agora fica muito mais simples de encontrar o erro :)

Espero ter ajudado.

Até a próxima!

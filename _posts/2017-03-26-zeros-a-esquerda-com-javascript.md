---
layout: post
published: false
title: Zeros a esquerda com Javascript
subtitle: 'Pad left com javascript :)'
date: '2016-06-16'
---
![](https://www.rascal.columbia.edu/images/jscript.gif)

E ae pessoas, blz?

Hoje tive um probleminha, tinha um número e precisava completar ele com zeros a esquerda...acho que vocês me entenderam, um numero 69 deveria ficar com 8 caracteres no total... então 00000069.

Como fazer isto, bom eu poderia ter feito, mas estava com um pouco de pressa então dei uma procurada no Google rapidinho e encontrei [este post](http://stackoverflow.com/a/11187738) no StackOverflow que me ajudou muito!

Bom basicamente ele faz um extend no objeto *Number* do JavaScript e adiciona um método *pad* (nome bem sugestivo) que recebe um parâmetro de quantidade de caracteres.


```
Number.prototype.pad = function(size) {
  var s = String(this);
  while (s.length < (size || 2)) {s = "0" + s;}
  return s;
}
```

Olhando para ele, parece perfeito, mas acho que falta somente um item para ficar ainda melhor, um parâmetro com o caractere que ele vai preencher esta string!

```
Number.prototype.pad = function(size, character = "0") {
  var s = String(this);
  while (s.length < (size || 2)) {s = character + s;}
  return s;
}
```

Pronto, nada demais, onde estava implementada vai continuar funcionando e fica mais personalizável.

Ah... mas como utilizar?

```

(69).pad(8); // 00000069
(66).pad(3, 6); // 666

```

Espero que vocês tenham achado interessante, pois eu achei e me ajudou bagarai!

Se tiver alguma sugestão, diga ai nos comentários!

Pra não perder o costume.. um *gifzinho* para animar ;)

![Sempre acontece.. kkk](http://geekshumor.com/wp-content/uploads/2013/09/Code-Refactoring.gif)

Me segue ai no [Twitter](http://twitter.com/lcomino) e também no [GitHub](http://github.com/lcomino).

Até mais!


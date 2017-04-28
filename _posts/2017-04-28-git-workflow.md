---
layout: post
published: true
title: Git Workflow
date: '2017-04-28'
---

Este texto não é meu, traduzi, para estudo do link abaixo.  
Fonte: https://github.com/thejameskyle/git-workflow/blob/master/README.md

Espero que ajude. ;)  




Este é um documento que venho trabalhando a algum tempo, já usei ele em vários equipes. Embora atenda a metodologia ágil, não é completamente amarrada a ela.

É necessário uma quantidade razoável de conhecimento em git/github/gitlab. Você pode certamente utilizar outras ferramentas para obter o mesmo resultado, mas provavelmente você terá que fazer algumas modificações.

## Iniciando

A regra mais importante deste workflow, é que o desenvolvedor que está escrevendo o código é responsável  por ter certeza que ele passa por todo o processo sem problemas e em tempo hábil.

Outros desenvolvedores podem chegar e ajudar de sempre que possível, até mesmo quando não é um trecho de código que ele trabalhou no passado ou o código é em alguma linguagem que ele não conhece. 

Embora isto possa parecer complicado, é bem verboso e provavelmente repete um monte de coisas que você já está fazendo. Pela minha experiência eu posso dizer que isto se tornará muito natural depois de um curto tempo, e você não perceberá mais isto tudo.

Claro que não existe uma única verdade para trabalhar com código em equipes, é um processo contínuo de melhoria do workflow existente. 

## Novo código

### Criando uma branch

1. Atualize **master**, **staging** e/ou **feature** branches para a ultima versão(ões)
  - Always branch from the place it will be merged back into
2. Crie uma branch 
  - nome curto e descritivo
  - iniciado com prefixos (eg. `lco_branch_name`)

### Realizando as alterações

3. Realize as alterações
  	- Tenha certeza que todas as tarefas estão sendo executadas (build, unit tests)
4. Test
  	- Rode um teste completo no projeto
5. Realize um commit com um nome descritivo
  	- inicie com `[WIP]` ("work in progress") se algum teste estiver quebrado

### Enviando as alterações

6. Verifique qualquer alteração na master
7. Faça o Rebase da branch na master
8. Remova qualquer `[WIP]` commits <<<< Squash any `[WIP]` commits
    - Tenha certeza que todos os commits façam sentido neste contexto
    - Não envie nenhum commit quebrado
9. Realize o push para o origin
    - Será criada uma nova branch no origin

### Pull Request/ Merge Request

10. Inicie o pull/merge request em uma **staging** ou **feature** branch
    - Coloque um titulo longo e descritivo na tarefa
    - Adicione uma lista com a descrição das alterações (changelog)
11. O servidor de CI deve executar os testes no pull request e alterar seu status
    - (ex. Travis CI)

### Revisão do código

12. Outros desenvolvedores devem analisar o código e deixar notas
    - analisar se o código está confuso
    - verificar possíveis problemas
    - qualquer melhoria no código
    - código está devidamente abstraído
    - ter certeza que os testes são apropriados e suficientes

13. O criador do código será o responsável por fazer pequenos ajustes e enviá-los novamente
    - Siga os mesmos passos do commit
14. Outros desenvolvedores deverão deixar um like no pull/merge request
    - Literalmente deixar um comentário com um emoji de thumbs up (`:+1:`)
    - e um breve texto do por que você está aceitando aquele código

### Revisão do código (alteração pequena necessária ou emergêncial)

Se existe qualquer pequena alteração a ser feita, uma que não afeta o código atual, o esta precisa ser realizada rapidamente, esta versão da revisão do código pode ser utilizada.

Se for uma emergência, solicite ajuda de outras pessoas imediatamente. Acredite, você mesmo irá cometer erros, e a última coisa que você quer fazer é gerar mais problema. Avise os membros do time que você está realizando esta alteração.

12. Revise o código você mesmo, ou tente solicitar alguem para verificar com você
    - tenha certeza que tudo está limpo
    - sem código confuso
    - verifique erros em potêncial
    - qualquer melhoria na estrutura
    - código devidamente abstraído
    - tenha certeza que realizou todos os testes
13. Realize qualquer alteração localmente e envie para o servidor, tenha certeza de revisar novamente o que você fez
    - Siga os passos do processo de commmit
14. Explique por que você precisa realizar o merge deste código, você mesmo. Deixe você mesmo um 'like'
    - Literalmente deixe um comentário com um like (`:+1:` on github)
    - e um pequeno texto do por que você está aceitando aquele pull request

### Juntando o código todo

Uma vez que o código foi revisado por todos, e você está confiante no codigo que você escreveu,e tudo está bem testado. Você poderã iniciar o processo de liberação.

15. Realize o merge do pull requeste dentro de uma **staging** ou **feature** branch no repositório oficial, e delete ela do github
16. Rode novamente a suite de testes no código da branch que recebeu o merge

### Liberando o código

Todo mundo tem seus próprios passos para realizar a liberação do código para produção, mas estas são algumas boas práticas:

17. Ter e adicionar dados da versão no arquivo de `CHANGELOG.md`
    - inclua o número da versão e a data de liberação
    - This can generally be done directly on staging since you shouldn't have any code that depends on the content of a markdown file
18. Realize o merge da **Staging** na **Master**
19. Realize a liberação da versão
    - criando uma nova tag de versão (semver)
20. Inicie o processo de atualização, e avise os interessados
    - Cruze seus dedos

## A Branch principal

A **Branch Principal** é sagrada, seu código deve estar sempre funcionando e estar sempre 'atualizável'. Você nunca deve trabalhar diretamente na master, e nunca deve realizar um push diretamente nela de uma versão local ou de qualquer outra branch. Você geralmente não deve realizar o push na **Master Branch** a não ser quando for realizar uma liberação de código para produção.

A branch master pode ser chamada de: `master`

## Branch de preparação (staging branch)

A **branch de preparação** é de onde você cria novas branchs e realiza o merge da maioria do seu código, deve sempre estar a frente do último release para a master e tentar sempre estar funcionando. Se algo quebrar, deve ser corrigido o mais rápido possível.

A branch de preparação pode ser chamada de: `staging`

## Branches de funcionalidades (feature branch)

Algumas vezes novas funcionalidades necessitam de vários membros do time para serem criadas, precisam realizar alterações no código em vários repositórios, ou levam um logo periodo de tempo para ser criadas. Nestes casos as **branches de funcionalidade (feature branch)** devem ser utilizadas.

Uma feature branch é similar a **staging branch** já que você nunca deve escrever código diretamente nela. Você fará pull requests nela antes de realizar o pull request no staging.

Se a feature branch estiver vinculada a outros repositórios então ela deve receber o mesmo nome e um link para estas branchs no pull request.

Branch de funcionliadade podem ser chamadas de: `feature_[branch_name]`

## Branches de desenvolvimento

Estas são as branches que você irá criar localmente e realizar o push para o origin. Elas podem ser removidas depois que for aceito o pull/merge request. Elas não precisam estar funcionando sempre, mas você irá trabalhar para isto.

Mantenha a suite de testes rodando, se muitas coisas começarem a sair fora do escopo de mudanças, entãi tenha certeza que as alterações são seguras a se fazer. Apenas use o seu melhor julgamento e tudo ficará bem.

Branches de trabalho ou desenvolvimento podem ser chamadas de: `iniciais_nome_branch`

## Spike Branches

**Spike branches** são codigos que você nunca deverá realizar merge. É descartável, código experimental para uma feature ou uma alteração rápida de código.

Geralmente serve para testar uma nova idéia, ou ver se é plausível implementar isto. Pode ser utilizado para tomar decisões de estrutura, ou para aprender sobre uma nova tecnologia.

Spike branches podem ser chamadas de: `spike_[branch_name]`

## Leitura adicional

- [A Successful Git Branching Model](http://nvie.com/posts/a-successful-git-branching-model/)
- [Understanding the Git Workflow](https://sandofsky.com/blog/git-workflow.html)
- [Github: Understanding the Git Flow](http://guides.github.com/overviews/flow/)
- [Issues with Git Flow](http://scottchacon.com/2011/08/31/github-flow.html)

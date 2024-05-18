# Trabalhando com Branchs (ramificações do master)

## O que é um Branch?
- Branch é a forma que o git separa as versões dos projetos;
- Quando um projeto é criado ele inicia na branch master;
- Geralmente cada nova feature de um projeto fica em um branch separado;
- Após a finalização das alteraçãoes, os branchs são unidos para ter o código-fonte final;

-> Um Branch é uma ramificação do nosso branch master:
>1. Existem alguns branchs que são bem comuns na área de desenvolvimento, algumas deles são: **branch dev** (onde ficam as features mais novas do projeto), **branch stage** (todos os recursos que vão entrar em produção em pouco tempo, e nele serão feitos todos os testes necessários).
>2. Nessa parte vamos criar um branch e depois que ele for aprovado poderemos unificar o branch.
>3. Uma versão separada do código para não bagunçar tudo.

## Criando e visualizando Branchs `git branch`
- Para visualizar os branchs disponíveis basta digitar `git branch`;
- Para criar um branch você precisa utilizar o comando `git branch nomeNovoBranch`;
- Estas operações são muito utilizadas no dia a dia de um dev;

-> Aqui nessa parte pode-se ver claramente como criar um branch via comando:
>1. Aqui estamos apenas criando um novo branch com o comando `git branch nomeNovoBranch`;
>2. Como esse foi nosso primeiro branch, ele foi criado a partir do master, mas se tentarmos
usar esse mesmo comando agora, ele vai criar um novo branch a partir do primeiro_branch, e 
isso não é interessante, o ideal é criar branchs sempre a partir do master;
>3. O comando `git branch` é como se fosse um `git status` dos branchs, pois ele lista no
terminal, todos os branchs que temos disponíveis atualmente no repositório;
>4. Quando é usado o comando `git branch nomeNovoBranch`, o git vai criar um novo branch a partir do 
branch que você está. Você pode ver ele usando o comando `git branch`.
>5. Criar e mudar para o branch criado no mesmo comando: `git checkout -b nomeBranchNovo`. 
✏️ Quando usamos esse comando, assim como o anterior iremos criar um novo branch igual ao que estamos.
Ou seja, se você está no branch "ajuste-home" e executa algum desses comandos descritos no item 4 e 5,
o branch criado será igual ao "ajuste-home".

## Deletando branches `git branch -d`
- Podemos deletar um branch com a flag `-d` ou `--delete` ou `-D`;
- Não é comum deletar um branch, normalmente guardamos o histórico do trabalho;
- Geralmente se usa o `delete` quando o branch foi criado errado;

-> Aqui você vai aprender a deletar branchs:
>1. Esse comando `git branch -d nomeBranch` ou `git branch --delete nomeBranch`, deve ser usado com cuidado, uma vez que quase nunca é utilizado por devs, já que os mesmos costumam guardar seus históricos de branchs para poder consultar quando for preciso. Esse comando geralmente se usa quando um branch é criado errado;
>2. Depois de fazer o comando, faça um `git branch` e confirme que o branch foi deletado.

## Mudando de Branch `git checkout`
- Podemos mudar para outro branch utilizando o comando `git checkout nomeBranch`;
- Este comando também é utilizado para dispensar mudanças de um arquivo;
- Alterando o branch podemos levar alterações que não foram commitadas junto, ⚠️ **TOME CUIDADO**.

-> Aqui vamos aprender alguns comandos para navegar entre os branchs:
>1. Mudar para um branch: `git checkout nomeBranch`.
>2. Antes de fazer um `git checkout nomeBranch`, é IMPORTANTE ver se foi tudo commitado no branch atual, pois caso não tenha sido, você levará a alteração que está fazendo para o branch que acabou de mudar. Um exemplo sério disso seria o seguinte: Suponha que você está fazendo uma alteração no branch `ajuste-home` e antes de commitar tudo que foi feito no branch, você faz um `git checkout master`, quando você fizer isso a sua alteração não commitada vai toda para o master e vai estar sendo feita direto no master, se você da um commit e um push, essa alteração que ainda não foi testada vai parar na master do repositório podendo causar grandes problemas uma vez que essa alteração ainda não foi validada.
>3. Criar e mudar para um branch no mesmo comando: `git checkout -b nomeBranchNovo`. Lembrando que ao fazer isso
o branch novo que será criado vai ser igual ao que você está. (observe o item 5 da segunda sessão)

## Unindo branchs `git merge`
- O código de dois branches distintos pode ser unido pelo comando `git merge nomeBranch`;
- Esse é outro comando para a lista dos mais utilizados;
- Normalmente é por meio dele que recebemos as atualizações de outros devs;

-> Aqui você vai usar o comando `git merge nomeBranch` para unir o seu branch com outro que você queira:
>1. Com esse comando é possível unir dois branchs em um só, ou seja, unir os códigos.
>2. Vamos supor que você esteja no branch `ajuste-home` e queira atualizar ele com o branch do seu colega, `ajuste-rodape`, que fez uma future nova e ainda não subiu para a master. Para fazer isso você deve 
fazer o seguinte: 
> - Dentro do branch `ajuste-home`, execute o comando: `git merge ajuste-rodape`
E fazendo isso tudo que o seu colega fez no branch dele será atualizado no seu.
>3. Uma coisa que é muito interessante fazer quando for iniciar o seu trabalho ou quando precisar atualizar o seu repo local é fazer o seguinte: `git merge master`
Fazendo isso você vai atualizar o seu repositório com o a última versão da master e vai saber que está 
trabalhando com a versão mais atual da master. 

 ⚠️ **NUNCA DÊ UM MERGE DO SEU REPOSITÓRIO COM A MASTER.ESSSE PROCESSO DEVE SER FEITO NO GITHUB.** ⚠️

## Usando o Stash `git stash`
- Podemos salvar as modificações atuais e prosseguir com uma outra abordagem
de solução e não perder o código;
- O comando para esta ação é o `git stash`;
- Após o comando o branch será resetado para a sua versão de acordo com o repo.

-> Com esse comando, você vai jogar o código que você fez no lixo para poder começar novamente:
>1. Esse código apagado poderá ser recuperado, isso será visto na próxima aula;
>2. Esse comando apaga os dados até o último commit feito.

## Recuperando Stashs `git stash apply`
- Podemos verificar as stashs criadas pelo comando `git stash list`;
- E também podemos recuperar a stash com o comando `git stash numeroStash(0,1,2,>3...)`;
- Desta maneira podemos continuar de onde paramos com os arquivos adicionados a stash:

-> Aqui você pode usar alguns comandos para recupar o código que colocou em stash(cash):
>1. O primeiro comando é o: `git stash list`. Esse comando trás uma lista das stashs que foram criadas;
>2. O segundo comando é o: `git stash apply numeroStash(0,1,2,>3...)`. Esse comando recupera a stash selecionada.
>3. O terceiro comando é o: `git stash show -p numeroStash(0,1,2,>3...)`. Esse comando te mostra no terminal o que tem na stash que selecionou.

## Removendo Stashs `git stash drop`
- Para limpar totalmente as stashs de um branch podemos utilizar o comando: 
`git stash clear`;
- Caso seja necessário deletar uma stash específica, podemos utilizar o comando: 
`git stash drop numeroStash(0,1,2,>3...)`

-> Aqui basicamente você pode usar esses comandos para remover as stashs. Não tem muito segredo.
>1. É importante ter cuidado na remoção da stash pois essa remoção é permanente.

## Usando Tags `git tag`
Aula que vi isso foi -> https://www.youtube.com/watch?v=CqJvlBXgCfc&ab_channel=RinaldoDev

- Tags são basicamente etiquetas dos seus commits;
- O comando para criar uma tag baseada no seu último commit é o:
` git tag -a nomeTag -m textoMensagem `
- Para criar uma tag baseada em um commit antigo, primeiro liste os commits com o comando:
` git log --pretty=oneline `
Feito isso você vai poder ver o id dos commits, e com eles criar a tag no commit que deseja.
Para criar essa tag baseada em um commit antigo use:
` git tag -a nomeTag idCommit(uma parte ou tudo) -m `textoMensagem` `
- Para apagar uma tag use:
` git tag -d nomeTag `
- O comando usado para listar as tags é o `git tag`.

-> Como já foi dito, a tag é como se fosse uma marcação para seu commit:
>1. Use as tags sempre que precisar para poder localizar mais facilmente o commit que deseja;<br>
>2. Se você quer entrar em um commit e ver, reverter e qualquer outra coisa no commit você pode marcar<br>
ele com uma tag e navegar para ele usando o checkout. Para mudar para uma tag use o comando:<br>
` git checkout nomeTag `<br>
>3. Simplificando a criação de tags:<br>
-Se você quer criar uma tag para seu último commit, faça o comando sem marcar o commit:<br>
` git tag -a nomeTag -m textoMensagem`<br>
-Se você quer expecíficar qual commit vai ter a tag, faça o comando marcando o commit:<br>
` git tag -a nomeTag idCommit(uma parte ou tudo) -m textoMensagem`<br>
>4. Se você quiser ver o que tem de alterações no commit que tem a sua tag, use:<br>
 `git show nomeTag `<br>
Ele vai te mostrar os dados do commit e da tag que foi criada.<br>

## Encontrando Branchs Remotos
- Branchs novos são criados a todo tempo e o seu git pode não estar mapeando eles;<br>
- Com o comando `git fetch` você é atualizado de todos os branchs e tags que ainda não estão reconhecidos por você;<br>
- Este comando é util para utilizar o branch de algum outro dev do time, por exemplo;<br>

-> Aqui vamos aprender a mapear branchs na nossa máquina:
>1. Usando o comando `git fetch` podemos buscar dentro do nosso repositório, novos branchs que foram enviados pelos outros devs do time;<br>
>2. Depois que você roda esse comando, ele vai te mostrar esse novo branch mas você ainda não vai ter acesso a ele. Para ter acesso a esse novo branch e poder contribuir com ele você deve fazer: `git checkout NomeBranchNovo`, feito isso você entrará no novo branch e poderá fazer atualizações nele usando o `git push`.
>3. Para ter certeza que está com o branch atualizado na sua máquina, sempre faça um `git pull` para poder trazer as atualizações. Atente-se que isso deve ser feito dentro do branch em questão, se for feito no master por exemplo, vai atualizar o master e não o nomeBranchNovo.

## Recebendo atualizações
- O comando `git pull` serve para recebermos atualizações do repositório remoto;<br>
- Cada branch poder ser atualizado com o `git pull`;<br>
- Utilizamos para atualizar a master do repositório como também quando trabalhamos em conjunto e queremos receber atualizações de um dev.

->Aqui vamos entender melhor sobre o comando `git pull`:
>1. Quando fazemos um `git pull`, estamos atualizando nossa máquina com a última versão do repositório que está no GitHub.
>2. Todo branch pode ser atualizado com o `git pull`, inclusive a master.
>3. É importante sempre usarmos esse comando para atualizar nossa máquina, quando vamos trabalhar em um repositório. Isso deve ser um costume.
>4. Sempre que for criar um novo branch, crie ele partir da master, sendo que a master deve estar 
atualizada com o `git pull`.

## Enviando alterações
- O comando `git push` faz o inverso do pull, ele envia as alterações para o repositório remoto:
- Serve também para enviar as atualizações de um branch específico para um outro dev:
- Ou quando terminamos uma tarefa e precisamos enviar ao repositório.

-> Com esse comando vamos atualizar o GitHub com nossas alterações:
>1. É importante lembrar que o git tem alguns estados:
>- Arquivos Untracked: ainda não trackeados no git, precisa de um `git add` e depois um commit.
>- Arquivos Modified: ainda não commitado, precisa de um commit para poder dar um push.
>2. É importante colocar no .gitignore tudo que não queremos enviar ao repositório,
pois não devemos enviar lixo ao repositório.

## Utilizando o remote
- Com o `git remote` podemos fazer algumas ações como: adicionar um repositório para trackear ou remover;<br>
- Quando criamos um repositório remoto, adicionamos ele ao git com o `git remote add orign enderecoLink`.

->Observe as anotações:
>1. Podemos usar o comando `git remote -v` para ver as nossa origens sempre que precisar;<br>
>2. Então para removermos o nosso link de repositório remoto, fazemos o seguinte comando: `git remote rm origin` Feito isso o git vai apagar a url onde ele manda os arquivos ou recebe atualizações do GitHub.
Se tentarmos fazer um `git pull` ou `git push`, o git vai nos retornar um erro, avisando que não tem mais uma servidor identificado para enviar ou receber atualizações. 
>3. Para adicionarmos o novo servidor, vamos fazer o seguinte: `git remote add origin https://linkrepositorio.com.br`
>Feito isso podemos voltar a trabalhar normalmente, usando pull, push e etc.

## Trabalhando com submódulos
- Submódulo é a maneira que temos de possuir dois ou mais projeots em um só repositório;<br>
- Podemos adicionar uma dependência ao nosso projeto atual, porém mantendo suas estruturas separadas;<br>
- Para adicionar o submódulo utilizamos o comando `git submodule add nomeRepo`; <br>
- Para verificar os submódulos o comando é o `git submodule`;<br>
- Para atualizar um submódulo, primeiro devemos commitar as mudanças;<br>
- E para enviar para o repositório do submódulo utilizamos o `git push --recurse-submodules=on-demand`;<br>
- Esse fluxo fará a atualização apenas do submódulo.

-> Basicamente é um projeto dentro de outro projeto:
>1. Podemos atualizar nossos submodulos, para fazer isso, basta entrar pelo terminal no repositório que está o seu submodulo e fazer um `git pull` e tbm um `git push` para poder enviar alterações.
>2. Para fazermos um git push no nosso submodulo, devemos fazer um comandinho um pouco diferente: `git push --recurse-submodules=on-demand`

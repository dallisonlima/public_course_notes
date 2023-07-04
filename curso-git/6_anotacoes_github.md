## Criando o Repositório
- No GitHub inicializamos os repositórios, e temos algumas informações importantes
para preencher, vamos vê-las em detalhes;
- Algumas delas são: Nome do repo, descrição, licença;
- Tudo poderá ser alterado ao longo do seu projeto, mas é interessante conhecer os
detalhes das informações para configurar um projeto;

-> Aqui vamos conhecer melhor a interface do GitHub, criando repos:
>1. Vá em Repositories;
>2. Aperte no botão verde NEW;
>3. Coloque o nome e a descrição;
>4. Selecione se o repo vai ser público ou privado;
>5. As opções abaixo vc pode add um readme.txt, um .gitignore etc.
>6. Ele vai te dar o passo a passo de como fazer a próxima etapa no vscode;
>7. Seleciona a pasta dos arquivos no VScode;
>8. Abre o terminal, e faça os comandos do passo a passo, linha por linha.
------------------------------------------------------------

## A aba CODE
- Na aba Code teremos acesso a informações importantes, como o próprio código fonte;
- Podemos checar também uma documentação do projeto pelo README.md;
- E os detalhes da licença do projeto;
- Criar branchs, adicionar arquivos e muito mais.
-------------------------------------------------------------

## A aba Issue
- Na aba Issue podemos criar tarefas ou possíveis bugs do projeto;
- Interessante para a organização se manter ciente do que precisa fazer ou corrigir;
- Normalmente há um padrão para criação de novos issues;
- Podemos utilizar o Markdown no texto também (igual o README.md);
- A issue deve ter um label e também um responsável;

-> Aqui, basicamente, vamos criar um thread de algum problema:
>1. Podemos usar lables para melhor padronizar e identificar as issues;
>2. Todos que tem acesso ao repo, poderão ver essas issues, comentá-las e etc;
>3. Aqui geralmente colocamos coisas que precisamos resolver com a rede de devs 
>que estão trabalhando no mesmo repo que nós.
---------------------------------------------------------------
## A aba Pull Request
- Na aba Pull Request é onde colaboradores do projeto enviam código
para resolver as issues ou adicionar novas funcionalidades ao projeto;
- A ideia é que o código não seja inserido direto na master e sim passe
por um pull request, para ser analisado;
- O pull request vem de um novo branch criado no projeot e enviado para 
o repo, com o incremento do código

-> Quando fazermos um pull request, estamos enviando para analise nossa att:
>1. De forma resumida o fluxo é o seguinte:
>    01. Abre seu editor;
>    02. `git pull`;
>    03. Cria seu branch;
>    04. Realiza sua alteração;
>    05. `git commit` e `git push`;
>    06. vai para o GitHub;
>    07. Chegando lá, abre a aba de Pull Request;
>    08. Cria sua pull request;
>    09. Analista olha e ve se tá tudo certo;
>    10. If(ok, merge com master)
>       if else(comenta oq vc tem que ajustar);
>2. Resumindo, depois que vc sobe sua alteração, vc cria um pull request para 
>verem se tá ok, e se estiver, enviam para o master, se não, comentam na issues
>ou no pull request para vc saber onde precisa ajustar o código.
-----------------------------------------------------

## A aba Actions
- Na aba Actions é onde se cria as automatizações de depoly com
integração em outros serviços;
- Incluindo CI/CD (Continuous Integration / Continuous Development);
- Ou seja, podemos criar uma rotina de atualizar a master automaticamente e outros
processos;

-> Nessa aba podemos automatizar deploys.<br>
>(ESTUDAR SEPARADAMENTE DEPOIS)
------------------------------------------------------

## A aba Projects
- Na aba Projects podemos criar um projeto e utilizar um quadro de tarefas;
- Este processo é conhecido como Kanban e pode ajudar a organizar seu time,
criando notas que podem virar issues.
- Estrutura interessante: Backlog, Retorno de qualidade, Desenvolvimento,
Teste, Finalizadas;
- A tela lembra muito o software Trello.

-> Basicamente é o Trello do GitHub:
>1. Podemos converter um card par auma issue.
-------------------------------------------------------

## Criando uma Wiki
- Na aba Wiki podemos criar uma documentação mais extensa para o projeto;
- Como descrever funcionalidades, bugs conhecidos e não solucionados, entre 
outras funções;
- A ideia é que seja um repositório de conhecimento sobre o projeto.

-> Aqui é uma wiki mesmo normal, igual eu uso na empresa, só que do GitHub:
>1. Aqui podemos colocar de tudo. O ideal é que tenha tudo na vdd.
--------------------------------------------------------

## A aba Insights
- Na aba Insights temos informações detalhadas do projeto, como:
- Quem são os contribuidores, commits, forks e muito mais;
- Interessante para entender como o projeto está andadndo e a sua evolução
desde o iniício;

-> Aqui temos basicamente um relatório do que está sendo feito no projeto:
>1. Aqui temos gráficos, tabelas, informações e tudo que precisamos para poder nos situar
>da melhor maneira no repositório;
>2. Podemos ver sobre a comunidade, sobre os contribuidores.
>3. Podemos ver sobre a quantidade de commits;
>4. Podemos ver sobre a quantidade de clones;
>5. Mostra sobre os forks, ou seja, quando alguém clona nosso repo dentro do GitHub dele.
----------------------------------------------------------

## A aba settings
- Na aba Settings temos acesso a diversas configurações do projeto;
- É onde podemos alterar o nome do repo ou remover/adicionar features;
- E também é nela que adicionamos colaboradores ao projeto;
- O repositório pode ser removido nesta aba.

-> Aqui vamos configurar o repo:
>1. Podemos habilitar ou não as issues, projects, wikis etc.
>2. Podemos remover branchs.
>3. Podemos deletar o repo.
>4. Podemos transferir para outro dono. 
>5. Podemos deixar ele privado ou público por aqui.
>6. Podemos gerenciar o acesso. É aqui que podemos convidar pessoas para o repo 
>na área de Manage access.
>7. Na área de segurança ele vai nos dar alertas de denpendencias e tals.
>8. Na área de branchs, podemos mudar o branch default.
>9. Tem mais coisas mas é só dar uma olhada que vc descobre oq é tudo.
-----------------------------------------------------

## Criando um Gist
- Gist são pequenos blocos de código que podem ser hospedados no GitHub tbm;
- Você pode armazenar uma solução que achou interessante para algum problema
e não quer perder, por exemplo;
- E o link do Gist pode ser compartilhado;
- No fim das contas o Gist acaba sendo um repositório também.

-> Aqui seria tipo uma wiki só que de tudo:
>1. Com os Gists podemos criar para deixar lá compartilhado, soluções de problemas,
>coisas que aprendemos e precisamos salvar, etc.
>2. Serve para vc compartilhar conhecimento.
------------------------------------------------------

## Buscando repositórios interessantes
- O GitHub não serve só para salvar os nossos projetos, podemos encontrar muitos repos
interessantes;
- Podemos até aprender com isso também, olhando o código fonte de desenvolvedores experientes;
- E não para por aí: você pode dar star nos projetos que gostou ou fork nos que deseja
continuar em um repo prórprio.

-> Aqui vc pode procurar tudo que precisa e muito mais.
>1. É um google dos códigos kk.
------------------------------------------------------

# FIM

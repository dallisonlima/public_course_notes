# Enviando um Repositório para o GH
- Podemos Facilmente enviar nossos repos para o GitHub; <br>
- Precisamos criar o projeto no GitHub, inicializar o mesmo no git em nossa máquina, sincronizar com o GitHub e enviar; <br>
- E esta sequência que parece ser complexa é facilmente executada por poucos comandos; <br>
- Vale lembrar que só fazemos uma vez por projeto este fluxo; <br>
- Porém alguns comandos utilizados vão ser úteis ao longo do curso. <br>

-> Para criar um projeto no GitHub:
>01. Vá em Repositories; <br>
>02. Aperte no botão verde NEW; <br>
>03. Coloque o nome e a descrição; <br>
>04. Selecione se o repo vai ser público ou privado; <br>
>05. As opções abaixo você pode add um readme.txt, um .gitignore; <br>
>06. Ele vai te dar o passo a passo de como fazer o próximo passo no vscode;
>07. Seleciona a pasta dos arquivos no VScode;
>08. Abre o terminal, e faça os comandos do passo a passo, linha por linha.
----------------------------------------------

# Verificando as Mudanças do projeto `git status`
- As mudanças do projeto podem ser verificadas por: `git status`; <br>
- Este comando é muito utilizado; <br>
- Aqui serão mapeadas todas as alterações do projeto; <br>
- Com é feito ? -> arquivos não monitorados e arquivos modificados; <br>
- Podemos também dizer que a diferença do que já está enviado ao servidor ou salvo no projeto, ou seja, tudo que aparece no `git status`, é pq ainda não foi upado no servidor.<br>

-> Estando dentro do terminal faça: `git status`; <br>
>1. Arquivos UNTRACKED: quando ainda não está sendo mapeado pelo git. <br>
>2. Se é feito uma modificação e essa mudança ainda não, foi enviada ao repo, ele (o arquivo) aparece como MODIFIED.(Esse já está no tracked) <br>
---------------------------------------------

# Adicionando arquivos ao projeto `git add` <br>
- Para adicionar arquivos a um projeto utilizamos o: `git add`; <br>
- Podemos adicionar um arquivo específico como também diversos de uma vez só; <br>
- Somente adicionadno arquivos eles serão monitorados pelo git; <br>
- É interessante utilizar este comando de tempos em tempos para não perder nada. <br>

-> Como adicionar um arquivo: <br>
>1. Se for um arquivo específico: `git add nomeArquivo`; <br>
>2. Se for para adicionar um arquivo em outra pasta: `git add direitorio/diretorio`; <br>
>3. Se quiser adicionar tudo de uma vez só: `git add .`. <br>
----------------------------------------------

# Salvando alterações `git commit` <br>
- As alterações salvas do projeto são realizadas pelo comando: `git commit`; <br>
- Podemos commitar arquivos específicos ou vários de uma vez com a flag `-a`; <br>
- É uma boa prática enviar uma mensagem a cada commit, com as alterações que foram feitas; <br>
- A mensagem pode ser adicionada com a flag `-m`. <br>
- ✏️ Para listar todos os seus commits use o comando:`git log --pretty=oneline`
- ✏️ Para navegar entre os commits use o comando:` git checkout idCommit `  <br>

|⚠️ Lembrando que isso é mais simples usando tags. (observe na sessão de tags do 2_anotacoes_branchs)|  <br>

-> Aqui basicamente vamos aprender a commitar (salvar a alteração):  <br>
>1. Quando damos um `git status` ele vai mostrar tudo verdinho, e isso significa que temos que commitar todos; <br>
>2. Para fazer um commit com mensagem, faça: `git commit -m "mensagem teste"`; <br>
>3. Para enviar um arvios específico: `git commit arquivo.txt -m "mensagem teste"`; <br>
>4. Para mandar todos os arquivos, faça: `git commit -a -m "mensagem teste"`; <br>
>5. Se você der um `git status` agora, não vai aparecer mais nada verdinho. <br>
----------------------------------------------

# Recebendo as mudanças `git pull`
- É comum também ter que sincronizar o local com as mudanças do remoto; <br>
- Esta ação é feita pelo comando `git pull` <br>
- Após o comando, serão buscadas atualizações, se encontradas elas serão unidas ao código existente na máquina local. <br>

-> Aqui você vai saber como receber mudanças no código, feitas por outros devs; <br>
>1. Se você der um `git pull`, e aparecer a mensagem **Already up to date**, significa que tudo já está atualizado. Faça esse comando frequentemente para ver se está usando a versão mais nova; <br>
>2. Vamos fazer o `git pull` para pegar tudo que tem de novo no GitHub, ou seja, atts. <br>
>3. Podem ser novos arquivos ou até mesmo pequenas atualizações. <br>
----------------------------------------------

# Enviando arquivos para o Servidor `git push`
- Quando finalizamos uma funcionalidade nova, enviamos o código ao repositório remoto, que é o código-fonte; <br>
- Esta ação é feita pelo `git push`; <br>
- Após esta ação o código do servidor será atualizado baseando-se no códido  local enviado. <br>

-> O comando para fazermos o envio de todo o código para o GitHub é o `git push`; <br>
>1. O estado ideal para enviar um código é quando fazemos um `git status` e não tem nada lá para você add ou commitar; <br>
>2. Se você der um `git status` e não aparecer nada, pode dar um `git push` e todos os seus arquivos serão atualizados no repositório remoto. <br>
-----------------------------------------------

# Clonando Repositórios `git clone`
- O ato de baixar um repositório de um servidor remoto é chamado de "clonar repositório". Para esta ação utilizamos o `git clone`; <br>
- Passando a referência do repositório remoto; <br>
- Este comando é utilizado quando entramos em um novo projeto, por exemplo. <br>

->Esse comando é feito para trazer os arquivos do repositório remoto para a máquina local; <br>
>1. Quando você entra em um novo projeto, deve pegar os arquivos upados no GitHub. <br>
>2. Para fazer isso deve-se usar o comando `git clone`; <br>
>3. Vamos no GitHub na área de download do código e selecionamos a url.  <br>
>4. Agora vamos no terminal e digitamos `git clone https://github.com/dallisonlima/curso_git_1.git `, e tudo que tem no repositório será trazido para minha máquina. <br> 
------------------------------------------------

# Removendo arquivos do repositório `git rm`
- Os arquivos podem ser deletados da monitoração do git; <br>
- O comando para deletar é o `git rm`; <br>
- Após deletar um arquivo do git ele não terá mais suas atualizações consideradas pelo git; <br>
- Apenas quando for adicionado novamente pelo `git add`. <br>

->Usando esse comando o arquivo é apagado do seu diretório; <br>
>1. Quando você usa o `git rm`, o arquivo é deletado do git e da sua pasta(repositório) consequentemente; <br>
>2. Quando isso é feito, é necessário que você envie essa att ao repositóio com o `git push`. <br>
>3. Para remover uma pasta, use `git rm -rf --cached nomePasta`.
------------------------------------------------

# Histórico de alterações `git log`
- Podemos acessar um log de modificações feitas no projeto; <br>
- O comando para este recurso é o `git log`; <br>
- Você receberá uma informação dos commits realizados no projeto até então; <br>

->Quando você estiver dentro do log, veja o seguinte: <br>
>1. Dentro do `git log`, você pode fazer o seguinte, ir dando enter e ver até a última (primeira), alteração que foi feita no seu projeto; <br>
>2. Para sair do `git log` dentro do windows aperte a tecla "q". No linux apert o "CTRL+C". <br>
--------------------------------------------------------------------

# Renomeando arquivos `git mv`
- Com o comando `git mv` podemos renomear um arquivo; <br>
- O mesmo também pode ser movido para outra pasta; <br>
- E isso fará com que este novo arquivo seja monitorado pelo git; <br>
- O arquivo anterior é excluído. <br>

->Com esse comando podermos fazer a alteração de diretório do arquivo, e também renomear; <br>
>1. Para fazer a alteração de diretório, podemos fazer da seguinte forma: <br>
>`git mv (diretorioatual\arqatual.txt) (diretorionovo\aruivoatual.txt)` <br>
>2. Para renomear um arquivo, faça da seguinte forma: <br>
>`git mv (diretorioatual\arqatual.txt) (diretorioatual\arquivonovo.txt)` <br>
---------------------------------------------

# Desfazendo Alterações
- O arquivo modificado pode ser retornado ao estado original; <br>
- O comando utilizado é o `git checkout`; <br>
- Após a utilização do mesmo o arquivo sai do staging; <br>
- Caso seja feita uma próxima alteração, ele entra no staging novamente. <br>

-> Esse comando pode ser utilizado para voltar ao estado original do arquivo no GitHub: <br>
>1. Quando você faz alguma coisa errada e quer voltar o arquivo que está mexendo para seu estado atual no GitHub, você deve usar esse comando; <br>
>2. Esse comando não funciona para arquivos já commitados; <br>
>3. Ao fazer esse comando todas as alterações feitas até o momento são apagadas(reseta) e o arquivo volta ao seu estado original. O comando deve ser feito assim: <br>
>`git checkout diretorioatual\arqatual.txt` <br>
-------------------------------------------------------------

# Ignorar arquivos no projeto ".gitignore"
- Uma técnica muito utilizada é ignorar arquivos do projeto; <br>
- Devemos inserir um arquivo chamado **.gitignore** na raiz do projeto; <br>
- Nele podemos inserir todos os arquivos que NÃO devem entrar no versionamento; <br>
- Isso é útil para arquivos gerados automaticamente ou arquivos que contêm informações sensíveis; <br>

-> Basicamente, tudo que é colocado nesse arquivo não vai ser mandado ao GitHub; <br>
>1. Crie na raiz um arquivo ".gitignore"; <br>
>2. Nesse arquivo pode-se adicionar o nome dos arquivos para que sejam ignorados.  <br>
>Observe o exemplo: <br>
>-teste.txt (aqui visando ignorar apenas um arquivo) <br>
>-node_modules/app.js (aqui visando ignora um arquivo de uma pasta) <br>
>-node_modules/* (aqui visando ignora todos os arquivo de uma pasta) <br>
--------------------------------------------------------------

# Desfazendo todas as aterações `git reset`
- Com o comando `git reset` podemos resetar as mudanças feitas; <br>
- Geralmente é utilizado com a flag --hard; <br>
- Todas as alterações commitadas e também as pendentes serão excluídas. <br>

-> Basicamente, quando é feito um `git reset` o código volta para o estado original: <br>
>1. Para fazermos um `git reset`, o comando deve ser feito assim: <br>
>`git reset --hard nomeBranch ` <br>
>2. Usando o **--hard**, todos os arquivos commitados também serão resetados. <br>
>3. O branch, é o repositório que vamos resetar, ou seja, quando selecionamos um branch, é lá que vamos puxar as informações para resetar. <br>
### ⚠️ (CUIDADO: ESSE COMANDO APAGA TODO O SEU CÓDIGO NÃO UPADO NO GITHUB) ⚠️ <br>
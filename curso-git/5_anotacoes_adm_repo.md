## Limpando arquivos untracked
- O comando `git clean` vai verificar e limpar arquivos que não estão sendo trackeados;
- Ou seja, todos que você não utilizou o `git add`;
- Utilizado para arquivos que são gerados automaticamente, por exemplo, e atrapalham a 
visualização do que realmente é importante.

-> Apaga arquivos untracked:
>1. É bom ficar atento para quando usar esse comando, ter certeza que tudo que você não quer
apagar, já tenha sido trackeado com o comando `git add` e por segurança, commitado também.

## Otimizando o repositório
- O comando `git gc` é uma abreviação de garbage collector;
- Ele identifica arquivos que não são mais necessários e os exclui;
- Isso fará com que o repositório seja otimizado em questões de performance.

-> Esse comando otimiza o repositório:
>1. Basicamente, quando esse comando é rodado, ele vai escanear o seu repositório local, vai pegar 
tudo que ele julgar desnecessário e vai apagar. 
>2. Esse comando deve ser usado bem de vez em quando, geralmente de mês em mês cada dev roda ele
na sua máquina. Pode ser usado tbm se os comandos estiverem demorando muito para responder quando
rodados.

## Checando integridade dos arquivos
- O comando `git fsck` é uma abreviação de File System Check;
- Esta instrução verifica a integridade de arquivos e sua conectividade;
- Verificando assim possíveis corrupções em arquivos;
- É um comando de rotina, utilizado para ver se está tudo certo com nossos arquivos.

-> Comando utilizado para vermos se está tudo bem com o repositório:
>1. É sempre bom utilizar ele de forma rotineira para verificarmos se está tudo ok;
>2. Pode ser utilizado junto ao `git gc`
>3. Esses comandos geralmente são feitos pelo gerênciador do repositório.

## Usando o comando REFLOG
- O `git reflog` vai mapear todos os seus passos no repositório, até uma mudança de branch é
inserida neste log;
- Já o `git log`, que vimos anteriormente, apenas armazena os commits de um branch;
- Os reflogs ficam salvos até expirar, o tempo de expiração padrão é de 30 dias.

-> Aqui é basicamente um `git log` com mais coisas:
>1. Muito bom para ver se você deu um checkout e levou coisas errada para um novo branch;
>2. Vai mostras resets, checkouts e tudo mais.

## Transformando o repositório para o arquivo
- Com o comando `git archive` podemos transformar o repositório um arquivo compactado, por exemplo;
- O comando é `git archive --format zip --output master_files.zip master`;
- E então a master vai estar zipada no master_files.zip.

->Observe as anotacoes abaixo:
>1. Entendendo o comando:<br>
>`git archive` (comando) <br>
>`--format zip` (definindo o formato como zip)<br>
>`--output master_files.zip` (definindo o arquivo externalizado pelo comando)<br>
>`master` (qual branch vai ser copiado. Geralmente é o master por ser o mais atualizado.)<br><br>
>Sendo assim, comando completo fica como o que está abaixo:<br>
>`git archive --format zip --output master_files.zip master`.<br>
>2. Feito esse comando, todos os arquivos do repositório serão salvos em um .zip no seu diretório.

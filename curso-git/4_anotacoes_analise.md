## Exibindo informações
- O comando `git show` nos dá diversas informações úteis;<br>
- Ele nos dá as informações do branch atual e também seus commits;<br>
- As modificações de arquivos entre cada commit também são exibidas;<br>
- Podemos exibir as informações de tags também usando o `git show nomeTag`.<br>

-> Esse comando nos trás informações úteis de um branch:<br>
>1. Basicamente quando esse comando é utilizado, ele vai nos trazer informações detalhadas do último commit feito no branch em questão;<br>
>2. Ele pode ser usado tando para branchs, quando para tags. Para usar ele com tags basta colocar o nome da tag na frente do `git show`, seria assim -> `git show nomeTag`.<br>
>3. Quando der esse comando e ele carregar, vc pode ir descendo com a setinha e ele vai te mostrando as informações.

## Exibindo diferenças
- O comando `git diff` serve para exibir as diferenças de um branch;<br>
- Quando utilizado as diferenças do branch atual com o remoto serão exibidas no terminal;<br>
- Podemos também verificar a diferença entre arquivos: `git diff nomeArquivo1 nomeArquivo2`;

-> Esse comando serve basicamente como um comparador de arquivos, branchs etc:<br>
>1. Se usarmos ese comando sozinho, ou seja, `git diff`, ele irá nos mostras as diferenças<br>
entre o branch que estamos e o repositório. <br>
>2. Para podermos usar esse comando comparando dois<br>
arquivos predestinados, devemos fazer assim -> `git diff nomeArquivo1 nomeArquivo2`;<br>
>3. Se os branchs estiverem iguais, ele não vai retornar nada no terminal;<br>
>4. Para comparar dois arquivos devemos fazer da seguinte forma:<br>
`git diff HEAD:note1.txt note2.txt`

## Log resumido
- O comando `git shortlog` nos dá um log resumido do projeto;
- Cada commit será unido por nome do autor;
- Podemos então saber quais commits foram enviados ao projeto e por quem.

-> Como o próprio nome já diz, trás uma rápida att do que já foi feito.<br>
>1. O `git shortlog`, trás um resumo de de commits e usuários para podermos saber<br>
tudo que aconteceu enquanto não estavamos trabalhando no projeto.
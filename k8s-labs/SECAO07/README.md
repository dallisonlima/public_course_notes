# MICROSERVIÇOS

## Escalabilidade
Escalabilidade vertical: É quando temos que aumentar a capacidade da máquina que estamos utilizand, por exemplo, aumentar a memória RAM ou espaço no HD.

Escalabilidade horizontal: É quando replicamos a mesma máquina ou serviço N vezes.

## Aplicação Monolítica
Uma aplicação monolítica é aquela na qual toda a base de código está contida em um só lugar, ou seja, todas as funcionalidades estão definidas no mesmo bloco. Geralmente este bloco é dividido em 3 partes:
* **Presentation -> Browser**
  * Onde o usuário vai acessar.
* **Business**
  * Camada que contém a lógica da aplicação. Nesta camada geralmente se encontram todas as bases de código, chamadas APIs e literalmente toda a inteligência do sistema.
* **Data Access <- Database**
  * Na camada de dados temos apenas as classes responsáveis pela conexão com o sistema de armazenamento de dados.

A arquitetura monolítica ainda é muito utilizada hoje e tem servido muito bem para a maioria das aplicações. Desta forma existem empresas que não pensam em migrar este modelo para qualquer outro porque ele simplesmente resolver o problema da empresa.

### Vantagens de Aplicações Monolíticas
* Simplicidade da arquitetura, pois não existem muitas camadas para se preocupar;
* Agregação de tecnologia, pois toda aplicação é desenvolvida em uma mesma tecnologia, facilitando a coesão da equipe;
* Fluxo de publicação simples, pois: Alterou -> Compilou -> É só publicar !
* Rápido desenvolvimento, pois já que usa uma arquiteura mais simples, o seu desenvolvimento tende a ser muito mais rápido.

## Aplicações em Microserviços
Com uma crescente utilização de APIs e rotas cada vez mais genéticas, o termo "escalabilidade" ganhou força de forma que seria possível escalar qualquer serviço através da escala horizontal.

As empresas começaram entrão a adotar uma prática pouco comum no ambiente de desenvolvimento: Quebrar a lógica de negócio em minúsculos pedaços independentes que se completam, criando uma espécie de rede de APIs internas totalmente ou parcialmente conectadas.

Uma das vantagens desta arquitetura é que agora era possível escalar qualquer tipo de serviço individualmente **sem a necessidade de escalar o ambiente todo** como era feito antes na arquitetura monolítica. 

### E o que é um microsserviço ?
Segundo Martin Fowler, microserviços é uma abordage que desenvolve um aplicativo único como uma suite de pequenos serviços.

Apesar da ideia de microserviços ser muito simples ao mesmo tempo é muito complicado de se desenvolver deformasustentável pois ao invés de lidar com um único “monstro” agora vamos dividí-lo em minúsculos “monstrinhos”. 

Em geral, um microserviço é um sistema simples, geralmente uma API, que se comunica através de HTTP. 

Uma característica importante dos microserviços é que eles podem, individualmente, serem desenvolvidos emumalinguagemde programação diferente, utilizando diferentes tecnologias de presistência de dados.

![Imagem](/SECAO07/img/exemplo.png)

### Vantagens de Aplicações Microserviços
- Arquitetura individual simples
- Mecanismo de comunicação universal e leve (HTTP); 
- Sistemas totalmente independentes; 
- Facilidade de deploy e testes unitários; 
- Ausência de um ponto de falha único;

### Desvantagens de Aplicações em Microserviços
- Se não for bem planejado e bem executado pode ser transformar em uma grande bagunça;
- A arquitetura geral pode se tornar complexa se não for bem documentada.

## Kubernetes e Microserviços
O Kubernetes é um sistema de orquestração de containers e é ideal para orquestração de microserviços pois é baseado 
totalmente em APIs.

O próprio Kubernetes é dividido em diversos micro-programas se tornando um microserviço.

Além de tudo é muito fácil de instalar, de usar e é agnóstico de infraestrutura podendo ser executado em diversos 
provedores.

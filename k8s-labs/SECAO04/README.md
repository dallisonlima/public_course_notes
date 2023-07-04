# Pods

Arquivo de criação de pods em YAML.
```yaml
apiVersion: v1
kind: Pod
metadata:
  name: aplicacao-pod
  labels:
    app: aplicacao
    tier: frontend
spec:
  containers:
    - name: nginx-container
      image: nginx
```
-------
# Replication Controler
Veja abaixo as estruturas de um arquivo de build do Replication Controller na linguagem YAML.

```yaml
  apiVersion: v1
  kind: ReplicationController
  metadata: #metadata do Replication Controller
    name: aplicacao-rc
    labels:
      app: aplicacao
      type: frontend
  spec: #spec do Replication Controller
    template:
      metadata: #metadata do Pod
        name: aplicacao-pod
        labels:
          app: aplicacao
          tier: frontend
      spec: #spec do Pod
        containers:
          - name: nginx-container
            image: nginx
    replicas: 2 #o numero definido aqui fala quantos pods tem que ter sempre ativos.
```
* Para criar use o mesmo comando para criar os pods.
```shell
kubectl create -f arquivo.yaml
```
* Para consultar a quantidade de replicas existentes.
```shell
kubectl get replicationcontroller
```
-------
# Replicaset
```yaml
  apiVersion: apps/v1 #sempre tem que ter essa /
  kind: ReplicaSet
  metadata: 
    name: aplicacao-rc
    labels:
      app: aplicacao
      type: frontend
  spec: 
    template:
      metadata: 
        name: aplicacao-pod
        labels:
          app: aplicacao
          tier: frontend
      spec: 
        containers:
          - name: nginx-container
            image: nginx

    selector: #indica qual pod dentre os existentes deve ser usado para ser replicado no cluster
      matchLabels:
        type: frontend
    replicas: 2 
```
* Para visualizar suas replicasets:
 ```shell
kubectl get replicaset
``` 
* Para deletar sua replicaset:
 ```shell
kubectl delete replicaset nome-replicaset
``` 
* Para criar use o mesmo comando para criar os pods.
```shell
kubectl create -f arquivo.yaml
```
* Para consultar a quantidade de replicas existentes.
```shell
kubectl get replicaset
```
-------
# Replication Controller vs Replicasets
Ambos tem o mesmo propósito, mas não são a mesma coisa.
O Replication Controller é mais antigo e está sendo substituido pelo ReplicaSet.

-------

# Escalando Aplicação
## 1 - Alterando o arquivo de configuração
Uma das formas é alterar no arquivo o número de replicas. Feito isso, temos que usar um comando de replace para que atualize meu cluster.

```shell
  kubectl replace -f arquivo.html
```
## 2 - Usando o ```kubectl scale```
Uma outra forma é usar o comando kubectl scale para fazer o **scaleup**. Veja o comando abaixo:

```shell
  kubectl scale --replicas=6 -f arquivo.yaml
```
**ou**

```shell
  kubectl scale nome-do-replicaset --replicas=6
```
Nesses comandos, informamos a nova quantidade de replicas através do parâmetro e ainda informamos qual é o arquivo (no primeiro caso) de definição ou nome do ReplicaSet (segundo caso) nos quais a definição está sendo alterada.

Para fazermos o **scaledown**, basta colocarmos o comando com um número de pods menor que o que está em execução. Por exemplo, se temos 6 pods Running, podemos usar o comando abaixo e o k8s vai matar 2 pods, deixando apenas 4 no final.
```shell
  kubectl scale nome-do-replicaset --replicas=4
```
## 3 - Especificando o objeto
Podemos especificar o objeto que será alterado. Veja o exemplo abaixo:

```shell
  kubectl scale --replicas=8 replicaset aplicacao-rs replicaset.apps/aplicacao-rs scaled
```
Veja que o nome do objeto replicaset deve ser o mesmo do objeto declarado.

<font color="red">Observação</font>   | 
--------- | 
Nenhum desses coamndos vistos nas opções acima altera o arquivo de configuração. Se deseja que o arquivo de configuração seja alterado, deve alterá-lo manualmente como mostrado na primeira opção de scaling.| 

-------

# Deployment
O deploymente é a publicação do nosso recurso na internet. Fazemos o deployment em vários containers para podermos dividir o acesso entre as máquinas. 

Podemos ter várias versões de deployments. Temos que atualizar nossos pods um por um até que todos estejam atualizados. Esse processo é chamado de ***rolling release/rolling updates***

Caso tenhamos algum problema durante a atualização do pod, temos que fazer um rollback, ou seja, voltar o pod para a versão antiga que estava funcionando.

Quando usamos um Deployment, automaticamente estamos criando um ReplicaSet através do Deployment.

## Arquivo de definição do Deployment
```yaml
  apiVersion: apps/v1 #sempre tem que ter essa /
  kind: Deployment
  metadata: 
    name: frontend-dp
    labels:
      app: frontend-app
      type: frontend
  spec: 
    template:
      metadata: 
        name: frontend-app
        labels:
          app: frontend-app
          tier: frontend
      spec: 
        containers:
          - name: nginx-container
            image: nginx
    selector: 
      matchLabels:
        type: frontend
    replicas: 3
```
*Comando para criação do Deployment:
```shell
kubectl create -f deployments/dp.yaml
```
*Comando para ver Deployments criados:
```shell
kubectl get deployment
```
## Atualizando e Desfazendo Depolyments
O ciclo de vida de uma aplicação inclui atualizações (updates) e durante estas atualizações coisas ruins podem acontecer sendo necessário desfazer estas atualizações.

As atualizações não são apenas atualizações da sua aplicação, podem também ser relacionadas a versão do Docker, Versão do K8S, configurações do cluster, do replicaset, lables, número de réplicas, ou seja, qualquer mudança ocorrida após a publicação original.

Se por exemplo mudamos a versão do nginx de nosso arquivo de Deployment, estamos fazendo uma atualização.

* Para aplicar a alteração, temos que usar o comando:
```shell
kubectl appply -f deployments/dp.yaml
```
Por baixo dos panos a ferramenta Deployment cria um novo ReplicaSet idêntico ao original e vai fazendo a atualização, um por um, se a estratégia for Rolling Update, ou todos de uma vez se a estratégia for Recreate.

## Estratégias de Deployment
#### 1 - Estratégia Recreate
Na estratégia Recreate, primeiro damos um shutdown em todas as máquinas. E então novas instâncias serão criadas.
O problema é que o sistema vai ficar fora do ar enquanto fazemos esse processo.
#### 2 - Estratégia Rolling Update (default)
Atualiza as instâncias de pods uma de cada vez, e dessa forma a aplicação vai estar sempre disponível, e com alta disponibilidade.

## Problemas de atualização
Podemos desfazer a atualização, voltando para a revision anterior, com o comando abaixo:
```shell
kubectl rollout undo deployments/frontend-dp
```
O rollback irá destruir as instâncias com a atualização e criar novamente instâncias com a versão anterior, de acordo com a estratégia de atualização adotada.

O comando com o rollout undo, é como se fosse o CTRL+Z do K8s.

Para voltar para uma **revision específica**:
```shell
  kubectl rollout undo deployment/frontend-dp --to-revision=x #sendo x o numero da revision
```

## Versionamento e rollout.
Quando realizamos o deploy com o Deployment do Kubernetes é disparado um recurso chamado "rollout". A cada execução do rollout é gerada uma nova revisão da publicação.

Esse processo de revisão, criado pelo "rollout" ajuda o Kubernetes a manter o rastro de publicações da aplicação, fazendo com que facilmente possa ser realizar um "rollback" para qualquer uma das revisões anteriores em caso de problemas.

* Qual comando usar para verificar o status do rollout:
```shell
kubectl rollout status deployment/frontend-dp
```
* Qual comando usar para verificar o histórico do rollout:
```shell
kubectl rollout history deployment/frontend-dp
```
-------

# Comandos importantes
**1 - Create** 
Esse comando serve para criar um deployment de acordo com o arquivo que foi criado e esta sendo passado dentro do comando, no caso é o frontend.yaml.
A flag *--record* serve para mostrar no comando ```kubectl rollout history deployment/frontend-dp``` qual comando foi usado para criar o deployment.

```shell
kubectl create -f frontend.yaml --save-config --record 
```

**2 - rollout**
Esse comando é muito útil pois vc pode ir vendo o deployment sendo criado e logo após a criação ser concluída vc tbm pode ser certinho se criou tudo ok.
```shell
kubectl rollout status deployment/frontend-dp
```
**3 - get all**
Informações gerais sobre o cluster k8s.
```shell
kubectl get all
```
**4 - rollout history**
```shell
kubectl rollout history deployment/frontend-dp
```
**5 - run**
Esse comando cria um pod com o nginx dentro de uma replicaset automaticamente.
```shell
kubectl run nginx --image=nginx
```
**6 - set image**
Esse comando atualiza a imagem dos containers diretamente pela CLI e essa flag *--record* vai salvar nas revisions o change-cause.
```shell
kubectl set image deployment frontend-dp frontend-container=nginx:1.18 --record
```

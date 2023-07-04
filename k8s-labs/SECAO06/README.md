# Conceitos de Serviços
Services no K8s premite a comunicação entre os diversos componentes de uma aplicação com o mundo externo á ela. Além disso permite que possamos conectar facilmente uma aplicação com outra e claro com usuários externos.
Os services permite que criemos uma aqruitetura de "microserviços" para uma aplicação.

* Comando para criar serviços
```shell
kubectl create -f service-definition.yaml
```

* Comando para criar serviços
```shell
kubectl get services
```
# Como acessar um pod por fora do cluster
Pods não possuem comunicação externa ao cluster.

O Service habilita uma porta de acesso para que possamos acessar o service e façamos o uso do serviço que estiver disponível.

# Tipos de service

## NodePort
Quando ouvir falar de serviço público já pensa no NodePort.

O NodePort abre uma comunicação entre o pod e agentes externos, como navegadores web se o serviço disponibilizado for web por exemplo.

Temos 3 portas envolvidas neste serviço:
* 30008 (<u>NodePort</u>) -> Faz a comunicação externa com o Service.

* 80 (<u>Service</u>) -> Porta que faz comunicação com o pod (**<u>Port</u>**)

* 80 (<u>Pod</u>) -> Porta do servidor web (**<u>Target Port</u>**)

**Obs.: No NodePort, temos que colocar o range entre 30000 - 32767.**

#### Arquivo de definição do NodePort
Veja abaixo:

```yaml
  apiVersion: v1
  kind: Service
  metadata:
    name: frontend-svc
  spec:
    selector:
      type: frontend
    ports:
      - name: http #opcional
        targetPort: 80 #opcional, fica igual o port
        port: 80
        nodePort: 30080 #opcional, pega uma aleatória se não definir
    type: NodePort #Aqui a definicao

```
Obs.: Caso "TargetPort" não seja informado irá assumir o mesmo valor de "port". E caso nodePort não seja informado irá assumir um valor aleatório dentro do range.

#### Comandos para ver ip do NodePort no minikube
* Pegar o ip do minikube
```shell
  minikube ip
```
* Pegar a url direta para acesso ao serviço que foi criado
```shell
  minikube service nameService --url
```

## ClusterIP
Quando falarmos de serviço privado, pensamos no ClusterIP
O ClusterIP é usado quando a comunicação entre os serviços é apenas interna (privada) ao cluster sem acesso à agentes externos.

O Service ClusterIP serve justamente para este fim, deixando a comunicação entre os pods funcionarem apenas internamente ao cluster, sem permitir o acesso externo.

Desta forma, podemos criar "microserviços" que juntos, farão parte de toda aplicação.

Cada "microserviço" recebe um nome e um endereço IP na qual deve ser usado pelos outros "microserviços" para realizar o acesso.

O frontend é a parte da aplicação que será acessada pelos usuários e desta forma precisa ter acesso externo. Assim, não podemos usar o ClusterIP aqui e sim o NodePort.

#### Arquivo de definição do ClusterIP
Veja abaixo:

```yaml
# exemplo para service do NGINX
  apiVersion: v1
  kind: Service
  metadata:
    name: backend
  spec:
    selector:
      type: backend
    ports:
      - name: nginx
        port: 80
    type: ClusterIP #Aqui a definicao
```
```yaml
# exemplo para service do REDIS
  apiVersion: v1
  kind: Service
  metadata:
    name: redis
  spec:
    selector:
      type: redis
    ports:
      - name: redis
        port: 6379
    type: ClusterIP #Aqui a definicao
```

## LoadBalancer
LoadBalancer habilita distribuição de carga entre os diversos pods que estão realizando o serviço. Este recurso _não funciona localmente, mas sim em provedores cloud_.

Muitas vezes sistemas que desenvolvemos podem receber uma quantidade muito grande de acessos precisando que a carga seja bem dividida entre os pods.

Para que a aplicação frontend seja acessível esternament ao cluster é necessário que criemos um serviço do tipo NodePort para que uma porta seja criada permitindo o acesso.

Uma forma de fazer isso, é usar serviços Cloud para criar o LoadBalancer.

Como o loadbalancer não funciona localmente, caso criemos localmente ele vai funcionar exatamente como um NodePort.

#### Arquivo de definição do LoadBalancer
Veja abaixo:

```yaml
  apiVersion: v1
  kind: Service
  metadata:
    name: frontend-svc
  spec:
    selector:
      type: frontend
    ports:
      - name: http
        targetPort: 80
        port: 80
        nodePort: 30042
    type: LoadBalancer
```

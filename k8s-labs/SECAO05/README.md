# Fundamentos Básicos de redes no K8s
Idealmente precisamos ter cada serviço dentro do seu próprio container.

Imagine por exemplo 2 containers com uma app java e um mysql. No Docker, teremos dois ips, um para cada container.

Quando um cluster nasce, ele tem dois ips, sendo um do próprio cluster (10.96.0.1) e outro da ApiServer (192.168.49.2).

No K8S quando quem recebe os ips são os PODs e não os containers. Cada POD recebe um ip distribuído pela rede central criada pelo k8s.

Em todo caso não é recomendável fazer a comunicação/acesso de um pod com outro através do endereço IP, pois este endereço pode mudar com a recriação do pod, que ocorre por exemplo com uma atualização. Veremos mais a frente como usar os nomes dos serviços para fazer a comunicação.

## KubeDNS
Dentre os serviços que são instalados junto com o K8S está o KubeDNS que faz toda a parte de tradução de nomes para endereços IP assim como um servidoer DNS normal.

Use o comando a seguir para ver se o serviço está running:
```shell
  kubectl cluster-info
```

# Multiplos Nodes
Cada máquina (node) vai ter um ip diferente, mas vão estar na mesma rede.

Podemos ter 2 clusters independentes, ou seja, eles não estarão vinculados à um mesmo cluster. Cada cluster tem seu próŕio endereço IP. Então eles podem se comunicar entre eles já que estão na mesma rede.

Inclusive, podem ter internamente o mesmo endereço IP no qual é usado para distribuir endereçamento IP para os PODs. Sendo que, os PODs de diferentes clusters podem ter o mesmo IP.

Isso porque não podemos ter entidades em uma mesma rede com um mesmo endereço IP, já que o endereço IP é usado não apenas como endereçamento mas também como identificador em uma rede.
Dessa forma ocorrerá um conflito de rede e o K8S não tem nenhuma ferramenta para ajustas este problema de forma automática.
O K8s espera que os operadores do cluster tenham conhecimentos mínimos de rede para que estes problemas não ocorram seguindo alguns critérios bem definidos.

## Critérios para evitar problemas de rede com o K8s
* Todos containers/PODs podem comunicar-se entre eles sem o uso de NAT.
* Todos os nodes podem se comunicar com todos containers e vice-versa sem o uso de NAT.
* Podemos usar Routing para resolver esses problemas

# Namespaces no K8s
Não é recomendado criar qualquer coisa dentro dos namespaces do K8S.

O problema de criar namespaces próprios ao invés de usar o namespace default do K8s é que você deverá lembrar e informar os namespaces próprios existentes sempre que for criar algo.

**Comandos para visualizar os namespaces:**
```shell
kubectl get namespaces
```
**Para visualizar tudo de um namespace:**
```shell
kubectl get all -n nome-Namespace
```
**Para criarmos um namespace:**
```shell
kubectl create namespace frontend --save-config
```
Ou podemos usar YAML:
```yaml
  apiVersion: v1
  kind: Namespace
  metadata:
    name: backend
```
Ai precisamos usar o seguinte comando:
```shell
kubectl create -f namespaces/backend.yaml --save-config
```
**Para consultarmos os namespaces existentes:**
```shell
kubectl get ns
```
**Criando Objetos no Namespace próprio em Kubernetes**
```shell
kubectl create -f pods/nginx.yaml --save-config --namespace=frontend
```
**Podemos criar um Namespace para ser o padrão do projeto**
```shell
kubectl config set-context --current --namespace=frontend
```
# Acessar um pod em um cluster K8s
Para acessar um pod podemos usar o seguint comando:
```shell
kubectl exec -it nome-do-pod -- bash
```
Dentro dele podemos fazer o que quiser como se fosse um servidor normal.

# KubeDNS
Esse serviço que fica rodando no cluster tem o objetivo de fazer a resolução dos nomes de serviços dentro do nosso cluster. Por exemplo, se um pod tem nome: pod-name-pod, quando chamarmos esse nome para conectar no pod ou algo assim, a resolução desse nome será feita pelo KubeDNS.

# FQDN (Fully Qualified Domain Name)

**kubernetes.default.svc.cluster.local**

* **kubernetes**    -> Nome do serviço
* **default**       -> Namespace padrão do kubernetes
* **svc**           -> Serviço (Kind: Service)
* **cluster.local** -> Nome do cluster na qual foi criado

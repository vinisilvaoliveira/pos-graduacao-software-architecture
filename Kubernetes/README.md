## Kubernetes

- Docker e Kubernetes
- EKS = Amazon Elastic Kubernetes Service
- Implementar o CI/CD no EKS e conceitos de segurança
- Arquitetura de software com conceitos de clean code

## O que é o Kubernetes?
O Kubernetes (também conhecido como k8s ou "kube") é uma plataforma de orquestração de containers open source que automatiza grande parte dos processos manuais necessários para implantar, gerenciar e escalar aplicações em containers.
	Componentes do Kubernets
	-Pod
	-Replica 7
	-Deploy
	-Volumes
	-hpa (helf check)
	-pv
	-ing
	-pvc
	-svc
	-sc
	-ds
	-quota
	

Azure = É uma plataforma de computação em nuvem executada pela Microsoft, que oferece acesso, gerenciamento e desenvolvimento de aplicativos e serviços por meio de data centers
- Camada de cache
redis chave valor( banco noSQL) um dos banco de dados mais rapidos, porém trabalha em memoria RAM

k6 = fazer teste de carga

kubectl apply -f [caminho]

PODS, RÓTULOS E ANOTAÇÕES 

## PODS:
 - Os Pods são criados a partir de definições YAML ou JSON, que especificam quais containers devem ser executados dentro do Pod, suas imagens e as portas em que cada container deve ouvir. Quando ele é criado, recebe um endereço IP interno dentro do cluster, permitindo que outros Pods se comuniquem com ele.
 - O Kubernetes gerencia a distribuição de carga de trabalho entre esses Pods de forma transparente para o usuário, garantindo que a carga seja distribuída de forma equilibrada.
  - Os Pods são importantes, no Kubernetes, porque permitem que os desenvolvedores criem aplicativos escaláveis e resilientes. Ao dividir os aplicativos em unidades menores, 
	como os Pods, os desenvolvedores podem se concentrar em escrever código para uma única responsabilidade. Além disso, os Pods permitem que os aplicativos sejam facilmente escalonados, 
	permitindo que eles lidem com variações de tráfego sem comprometer o desempenho.

## ROTULO:
 - Os rótulos e as anotações são recursos importantes no Kubernetes, para gerenciar e organizar os objetos, incluindo os Pods.
 - Os rótulos são pares de chave-valor que são atribuídos aos objetos no Kubernetes, como Pods, Serviços, Application Controllers, entre outros. Eles são usados para identificar, categorizar e selecionar objetos para operações de gerenciamento, como escalonamento e exclusão. Por exemplo, você pode adicionar um rótulo "app: myapp" ao seu Pod para indicar que ele faz parte da aplicação "myapp". Você pode usar esses rótulos para selecionar e executar operações em todos os Pods que fazem parte dessa aplicação.

## ANOTAÇÕES:
As anotações, por outro lado, são pares de chave-valor opcionais que podem ser adicionadas a objetos no Kubernetes. Eles são usados para adicionar metadados adicionais aos objetos, como informações de depuração, documentação e políticas de segurança. Por exemplo, você pode adicionar uma anotação "author: Thiago S Adriano" ao seu Pod para indicar que ele foi criado por Thiago S Adriano. Essas anotações não são usadas para seleção de objetos, mas podem ser úteis para fins de documentação e auditoria.


- Services e Config-Map
Os Services são recursos importantes do Kubernetes, que permitem que você exponha serviços dentro do cluster Kubernetes e gerencie o acesso a esses serviços de forma eficiente.
Um Service é um objeto do Kubernetes que permite que você exponha um conjunto de Pods como um serviço. Ele fornece um único ponto de entrada para acessar esses Pods, permitindo que você gerencie o acesso a esses serviços de forma eficiente. O Service é responsável por distribuir o tráfego entre os Pods do serviço, garantindo que o tráfego seja distribuído de forma justa e que a carga seja balanceada.

 - ClusterIP: Este é o tipo padrão de Service no Kubernetes. Ele expõe o serviço em um endereço IP interno do cluster e é acessível apenas dentro do cluster Kubernetes. É útil para serviços que precisam se comunicar com outros serviços dentro do cluster Kubernetes
 - NodePorte: este tipo de Service expõe o serviço em um número de porta no nó do cluster Kubernetes. Isso permite que o serviço seja acessível fora do cluster usando o endereço IP do nó e a porta atribuída. É útil para serviços que precisam ser acessados fora do cluster, como aplicativos da web.
 - LoadBalace: este tipo de Service expõe o serviço em um balanceador de carga externo. Isso permite que o serviço seja acessível fora do cluster usando um endereço IP externo e uma porta atribuída. É útil para serviços que precisam ser acessados de fora do cluster Kubernetes e exigem balanceamento de carga.
 
Exemplo em aula: Criamos um arquivo com extensão YAML
apiVersion: a versão da API do Kubernetes que está sendo usada. Neste caso, v1.
kind: o tipo de objeto Kubernetes que estamos criando. Neste caso, um Pod.
metadata: as informações de metadados sobre o Pod, incluindo o nome do Pod.
spec: as especificações do Pod, incluindo informações sobre os containers que serão executados dentro do Pod.
containers: uma lista de containers que serão executados dentro do Pod. Neste exemplo, há apenas um container.
name: o nome do container. Neste exemplo, o nome é "meu-container".
image: a imagem do container que será usada. Neste caso, a imagem do Nginx.
ports: as portas que serão expostas pelo container. Neste exemplo, a porta 80 é exposta.

## ConfigMaps
 - O ConfigMap é um recurso do Kubernetes que permite separar as configurações de um container de seus artefatos de implantação. Isso significa que é possível armazenar as configurações em um local centralizado e gerenciá-las separadamente do container.
 kubectl create configmap my-service-config --from-file=config.yaml
 
## REPLICASETS
  - ReplicaSets é um objeto do Kubernetes que garante que um número específico de réplicas de um conjunto de Pods esteja em execução a qualquer momento.  Ele monitora o status das réplicas de um Pod e, se alguma réplica falhar, inicia uma nova para substituí-la.
  - Conforme vimos no exemplo anterior, os ReplicaSets são responsáveis por manter a integridade do estado do aplicativo, garantindo que haja um número mínimo de réplicas em execução em todos os momentos. Eles são uma extensão do conceito de Deployment que também aprenderemos nesta aula, e que permitem gerenciar o número de réplicas de um conjunto de Pods e atualizar o aplicativo para uma nova versão.
  - Os ReplicaSets também são responsáveis pela seleção dos Pods que fazem parte do conjunto. Eles usam um seletor de rótulo (que aprendemos na aula anterior), para definir quais Pods pertencem ao conjunto. 
  
 ## Deployments
  - Um Deployment é um objeto Kubernetes que gerencia a implantação de um conjunto de réplicas de um aplicativo. Ele fornece recursos para gerenciar a atualização de aplicativos, rollbacks e dimensionamento horizontal.
  - O Deployment é responsável por garantir que um conjunto específico de réplicas esteja em execução em um determinado momento.
  - Outra funcionalidade importante do Deployment é o dimensionamento horizontal. Isso permite que os usuários aumentem ou diminuam o número de réplicas do aplicativo com base na demanda do serviço. Isso é particularmente útil para aplicativos que experimentam flutuações na carga de trabalho.
  ![kubectl.PNG](..%2F..%2Fmodulo%201%20kubernetes%2Fkubectl.PNG)
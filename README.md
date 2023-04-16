
Tipos mais usados

Pod: define um único contêiner e seus volumes.

Deployment: define uma implantação gerenciada de um conjunto de réplicas de um conjunto de pods.

Service: define um serviço de rede que expõe um conjunto de pods usando um endereço IP e um nome de DNS.

Namespace: define um espaço de nomes lógico usado para isolar recursos em um cluster Kubernetes.

ConfigMap: fornece um mecanismo para injetar dados de configuração em um contêiner.

Secret: fornece um mecanismo para injetar dados confidenciais em um contêiner.

PersistentVolume: define uma unidade de armazenamento de dados que persiste após a exclusão do pod.

PersistentVolumeClaim: define uma solicitação de armazenamento de dados de um pod.

StatefulSet: define um conjunto de réplicas de pods com identidades únicas e persistência de dados.

DaemonSet: define um conjunto de réplicas de pods que são implantados em todos os nós de um cluster.

Job: define um trabalho que é executado até a conclusão com uma ou mais réplicas de pods.

CronJob: define um trabalho que é executado periodicamente em um intervalo definido.

Ingress: é um objeto do Kubernetes usado para definir regras de roteamento de tráfego HTTP ou HTTPS para serviços em um cluster Kubernetes. Ele atua como uma camada de abstração entre serviços expostos e o tráfego externo, permitindo que o tráfego seja roteado para diferentes serviços com base em regras de host e caminho. O Ingress é um recurso nativo do Kubernetes que pode ser usado com vários controladores de Ingress diferentes, como Nginx, Traefik, Istio, entre outros. O controlador de Ingress é responsável por implementar as regras de roteamento definidas no objeto Ingress e, portanto, o comportamento do Ingress pode variar dependendo do controlador que está sendo usado

------
Deployment configuration for SonarQube. At this stage, we need to do a little trick in configuring SonarQube. One of the configurations needed to run SonarQube in a Linux environment is to increase the maximum amount of virtual memory by changing the value of max_map_countto 524288. If SonarQube is deployed on a VM, this might not be a big deal as we can change it permanently. But in Kubernetes, it takes a bit of an extra step so this configuration can continue to be applied when pods are created

kubectl apply -f .\postgress-pvc.yaml
kubectl apply -f .\postgress-configMap.yaml
kubectl apply -f .\postgress-service.yaml
kubectl apply -f .\postgress.yaml

kubectl apply -f .\sonar-pvc.yaml
kubectl apply -f .\sonar-configMap.yaml
kubectl apply -f .\sonar-service.yaml 
kubectl apply -f .\sonar.yaml 

TLS
kubectl create secret tls my-fancy-certs — key ssl.key — cert ssl.crt -n sonar

Sonar default user admin password admin
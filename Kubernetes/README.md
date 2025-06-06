# Kubernetes

## Índice:

1. [Kubernetes](#kubernetes-comandos)
1. [Modo Declarativo](#modo-declarativo)
1. [Minikube](#minikube)

## Kubernetes Comandos:

- **Criando um deployment:**

  ```bash
  kubectl create deployment <NOME> --image=<IMAGEM>
  ```

  - **OBS!** A imagem precisa estar no Docker Hub.

- **Checando o deployment:**

  ```bash
  kubectl get deployments
  ```

- **Detalhes do deployment:**

  ```bash
  kubectl describe deployments
  ```

- **Checando os pods:**

  ```bash
  kubectl get pods
  ```

- **Detalhes dos pods:**

  ```bash
  kubectl describe pods
  ```

- **Obtendo configurações do Kubernetes:**

  ```bash
  kubectl config view
  ```

- **Criando um serviço:**

  ```bash
  kubectl expose deployment <NOME> --type=<TIPO> --port=<PORT>
  ```

  - **OBS!** O `type`, geralmente, é do tipo `LoadBalancer`.

- **Checando os serviços:**

  ```bash
  kubectl get services
  ```

- **Detalhes dos serviços:**

  ```bash
  kubectl describe services/<NOME>
  ```

- **Replicando à aplicação:**

  ```bash
  kubectl scale deployment/<NOME> --replicas=<NUMERO>
  ```

- **Checando o número de réplicas:**

  ```bash
  kubectl get rs
  ```

- **Diminuindo à aplicação:**

  ```bash
  kubectl scale deployment/<NOME> --replicas=<NUMERO_MENOR>
  ```

- **Atualizando a imagem dos pods:**

  ```bash
  kubectl set image deployment/<NOME> <NOME_CONTAINER>=<NOVA_IMAGEM>
  ```

- **Desfazendo alterações:**

  ```bash
  kubectl rollout status deployment/<NOME>
  ```

- **Para voltar as alterações:**

  ```bash
  kubectl rollout undo deployment/<NOME>
  ```

- **Excluir um serviço:**

  ```bash
  kubectl delete service <NOME>
  ```

- **Excluir um deployment:**

  ```bash
  kubectl delete deployment <NOME>
  ```

## Modo Declarativo:

### Principais chaves:

- **apiVersion:** Especifica a versão da API Kubernetes usada para o recurso.
- **kind:** Difine o tipo do recurso que está sendo criado (pod, service, deployment, ...).
- **metadata:** Contém metadados sobre o objetivo.
  - **name:** Nome do recurso.
  - **namespace:** Namespace onde o recurso será criado.
  - **labels:** Rótulos usados para organização e seleção.
  - **annotations:** Informações adicionais para o recurso.
- **spec:** Define as especificações desejadas para o recuso. Pode depender do tipo do recurso (deployment, service ou pods).

### Especificações Comuns Para Recursos:

#### Pod:

- **containers** (dentro de `spec`): Define os contêiners do pod.
  - subschaves:
    - **name:** Nome do contêiner.
    - **image:** Imagem do contêiner.
    - **ports:** Portas expostas pelo contêiner.
    - **env:** Variáveis de ambiente.
    - **volumeMounts:** Montagem de volumes.

#### Deployment:

- **replicas:** Define o número desejado de réplicas.
- **selector:** Define o critério para associar pods ao deployment.
- **template:** Define o modelo de pod para os pods gerados pelo deployment.

#### Service:

- **type:** Define o tipo do serviço (`ClusterIP`, `NodePort`, `LoadBalancer`).
- **ports:** Define as portas do serviço.
  - **port:** Porta exposta pelo serviço.
  - **targetPort:** Porta do contêiner alvo.
- **selector:** Defie os rótulos usados para direcionar o tráfego para os pods corretamente.

### Exemplo de modo declarativo:

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: my-deployment
  labels:
    app: my-app
spec:
  replicas: 3
  selector:
    matchLabels:
      app: my-app
  template:
    metadata:
      labels:
        app: my-app
    spec:
      containers:
        - name: my-container
          image: nginx:latest
          ports:
            - containerPort: 80
---
apiVersion: v1
kind: Service
metadata:
  name: my-service
  labels:
    app: my-app
spec:
  selector:
    app: my-app
  ports:
    - protocol: TCP
      port: 80
      targetPort: 80
  type: ClusterIP
```

### Comandos:

- **Executando arquivo de deployment:**

  ```bash
  kubectl apply -f <ARQUIVO>
  ```

- **Parando o deployment:**

  ```bash
  kubectl delete -f <ARQUIVO>
  ```

- **Executando o serviço:**

  ```bash
  kubectl apply -f <ARQUIVO>
  ```

- **Parando o serviço:**

  ```bash
  kubectl delete -f <ARQUIVO>
  ```

## Minikube:

- **Iniciando o Minikube:**

  ```bash
  minikube start --driver=<DRIVER>
  ```

  - O driver pode ser `virtualbox`, `hyperv` ou `docker`.

- **Verificando status do Minikube:**

  ```bash
  minikube status
  ```

- **Parando o Minikube:**

  ```bash
  minikube stop
  ```

- **Acessando a dashboard do Kubernetes:**

  ```bash
  minikube dashboard
  ```

- **Gerando IP de acesso:**

  ```bash
  minikube service <NOME>
  ```

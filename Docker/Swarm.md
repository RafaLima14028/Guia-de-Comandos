## Docker Swarm:

- **Iniciando o Docker Swarm:**

  ```bash
  docker swarm init --advertise-addr <IP_DO_NODE>
  ```

- **Listando nodes ativos:**

  ```bash
  docker node ls
  ```

- **Adicionando nodes:**

  ```bash
  docker swarm join --token <TOKEN> <IP>:<PORTA>
  ```

- **Subindo novo serviço:**

  ```bash
  docker service create --name <NOME> <IMAGEM>
  ```

- **Listando os serviços:**

  ```bash
  docker service ls
  ```

- **Removendo os seviços:**

  ```bash
  docker service rm <NOME>
  ```

- **Escalando as réplicas:**

  ```bash
  docker service create --name <NOME> --replicas <NUMERO> <IMAGEM>
  ```

- **Checando token do Swarm:**

  ```bash
  docker swarm join-token manager
  ```

- **Checando o Swarm:**

  ```bash
  docker info
  ```

- **Removendo instância do Swarm:**

  ```bash
  docker swarm leave
  ```

- **Removendo um node:**

  ```bash
  docker node rm <ID>
  ```

- **Inspecionando serviços:**

  ```bash
  docker service inspect <ID>
  ```

- **Verificar containers ativados pelo serviço:**

  ```bash
  docker service ps <ID>
  ```

- **Rodando o Compose com Swarm:**

  ```bash
  docker stack deploy -c <ARQUIVO.YAML> <NOME>
  ```

- **Aumentando réplicas do Stack:**

  ```bash
  docker service scale <NOME>=<REPLICAS>
  ```

- **Fazer serviço não receber mais Tasks:**

  ```bash
  docker node update --availability
  drain <ID>
  ```

- **Atualizando parâmetros:**

  ```bash
  docker service update --image <IMAGEM> <SERVICO>
  ```

- **Criando rede:**

  ```bash
  docker network create --driver overlay <REDE>
  ```

  Conectar com:

  ```bash
  docker service create --name <REDE> --replicas <NUMERO> --network <NOME_REDE> <IMAGEM>
  ```

  ou

  ```bash
  docker service update --network
  <REDE> <NOME>
  ```

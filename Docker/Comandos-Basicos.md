## Comandos Básicos:

- **Listar contêineres em execução:**

  ```bash
  docker ps
  ```

  ou

  ```bash
  docker container ls
  ```

  _Para ver todos, incluindo os parados:_ `docker ps -a`

- **Executar um contêiner a partir de uma imagem:**

  ```bash
  docker run [IMAGEM]:[TAG]
  ```

  - _Para executar em segundo plano:_ adicione `-d`

  - _Para fazer bind da porta_: adicione `-p [PORTA]:[PORTA]`

  - _Para remover o container quando parar:_ adicione `--rm`

  - _Para executar o container em modo iterativo:_ adicione `-it`

  - _Para adicionar um nome ao container:_ adicione `--name [NOME_DO_CONTAINER]`

- **Acessar o shell de um contêiner em execução:**

  ```bash
  docker exec -it [NOME_OU_ID_CONTAINER] bash # ou sh, dependendo da imagem
  ```

- **Verificar logs de um contêiner:**

  ```bash
  docker logs [NOME_OU_ID_CONTAINER]
  ```

- **Iniciar/Parar um contêiner:**

  ```bash
  docker start [NOME_OU_ID_CONTAINER]
  docker stop [NOME_OU_ID_CONTAINER]
  ```

- **Remover um contêiner (deve estar parado):**

  ```bash
  docker rm [NOME_OU_ID_CONTAINER]
  ```

- **Copiando arquivos entre containers:**

  - **Colocar arquivos no contêiner:**

    ```bash
    docker cp [ARQUIVO_NO_HOST] [NOME_CONTAINER]:[CAMINHO_DESTINO_NO_CONTAINER]
    ```

  - **Pegar arquivos do contêiner:**
    ```bash
    docker cp [NOME_CONTAINER]:[CAMINHO_DESTINO_NO_CONTAINER] .
    ```

- **Vericar informações de processamento:**

  ```bash
  docker top [NOME_OU_ID_CONTAINER]
  ```

- **Vericar dados de um container:**

  ```bash
  docker inspect [NOME_OU_ID_CONTAINER]
  ```

- **Vericar os processos em um container:**
  ```bash
  docker stats [NOME_OU_ID_CONTAINER]
  ```

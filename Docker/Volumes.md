## VOLUMES

- **Listando os volumes:**

  ```bash
  docker volume ls
  ```

- **Criando um volume anônimo:**

  ```bash
  docker run -v <PASTA_NO_CONTAINER>
  ```

  - A flag `-v` serve para criar um volume no Docker.

- **Criando um volume nomeado:**

  ```bash
  docker run -v <NOME_DO_VOLUME>:<PASTA_NO_CONTAINER>
  ```

  - A flag `-v` serve para criar um volume no Docker.

- **Criando um volume bind mount:**

  ```bash
  docker run -v <PASTA_NO_HOST>:<PASTA_NO_CONTAINER>
  ```

  - A flag `-v` serve para criar um volume no Docker.

- **Criando um volume nomeado manualmente:**

  ```bash
  docker volume create <NOME_DO_VOLUME>
  ```

- **Inspecionando um volume:**

  ```bash
  docker volume inspect <NOME_DO_VOLUME>
  ```

- **Removendo um volume:**

  ```bash
  docker volume rm <NOME_DO_VOLUME>
  ```

- **Criando um volume apenas de leitura:**

  ```bash
  docker run -v <NOME_DO_VOLUME>:<PASTA_NO_CONTAINER>:ro
  ```

  - A flag `-v` serve para criar um volume no Docker.
  - `ro` é uma abreviação para read-only.

### Tipos de volumes:

- **Anônimos (anonymous):** Diretórios criados pela flag `-v` (no comando `run`), porém com um nome aleatório;

- **Nomeados (named):** São volumes com nomes, podemos nos referir a estes facilmente e saber para que são utilizados no nosso ambiente;

- **Bind Mounts:** Uma forma de salvar dados na nossa máquina, sem o gerenciamento do Docker, informamos um diretório para este fim;

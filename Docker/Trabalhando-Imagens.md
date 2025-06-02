## Trabalhando com Imagens:

- **Listar imagens:**

  ```bash
  docker images
  ```

  ou

  ```bash
  docker image ls
  ```

- **Construir uma imagem a partir de um Dockerfile (no diretório atual):**

  ```bash
  docker build -t <NOME_MINHA_IMAGEM>:<TAG> .
  ```

  - A flag `-t` serve para nomear a imagem no momento em que ela é montada.

- **Baixar imagem do Hub:**

  ```bash
  docker pull <IMAGEM>:<TAG>
  ```

- **Renomear a imagem:**

  ```bash
  docker tag <NOME>
  ```

- **Removendo uma imagem:**
  ```bash
  docker rmi <NOME_DA_IMAGEM>
  ```

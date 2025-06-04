## Docker Compose:

### Comandos:

- **Rodando um compose:**

  ```bash
  docker compose up
  ```

  - O `-d` permite executar em segundo plano

- **Parando um compose:**

  ```bash
  docker compose down
  ```

### Variáveis de ambiente:

1. Criar um env file (**.env**) contendo as variáveis;
2. Dentro do docker-compose.yaml, usar a sintax: `${VARIAVEL}`;

### docker-compose.yaml:

- **version:** Define a versão do formato do arquivo Compose para determinar os recursos disponíveis.
- **services:** Lista os serviços da aplicação, cada um representando um container.
  - **image:** Especifica a imagem Docker a ser usada pelo serviço.
  - **container_name:** Define um nome customizado para o container do serviço.
  - **environment:** Permite configurar variáveis de ambiente dentro do container.
  - **volumes** _(dentro de services)_ **:** Define volumes usados pelo serviço para persistência ou compartilhamento de dados.
  - **networks** _(dentro de services)_ **:** Define as redes nas quais o serviço será conectado.
  - **build:** Especifica o contexto e as configurações para construir a imagem Docker do serviço.
- **volumes** _(fora de services)_ **:** Declara volumes reutilizáveis para serviços.
- **networks** _(fora de services)_ **:** Declara redes personalizadas para conectar os serviços.

### Exemplo:

```yaml
version: "3.9"

services:
  app:
    image: node:16
    container_name: my_app
    build:
      context: ./web
      dockerfile: Dockerfile
    ports:
      - "3000:3000"
    environment:
      - NODE_ENV=${env}
      - PORT=${port}
    volumes:
      - ./app:/usr/src/app
    networks:
      - app_network

  db:
    image: postgres:13
    container_name: my_database
    environment:
      POSTGRES_USER: myuser
      POSTGRES_PASSWORD: mypassword
      POSTGRES_DB: mydb
    volumes:
      - db_data:/var/lib/postgresql/data
    networks:
      - app_network

volumes:
  db_data:

networks:
  app_network:
    driver: bridge
```

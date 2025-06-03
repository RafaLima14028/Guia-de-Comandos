## Networks:

- **Listar todas as redes:**

  ```bash
  docker network ls
  ```

- **Criando uma rede:**

  ```bash
  docker network create <NOME>
  ```

- **Removendo uma rede:**

  ```bash
  docker network rm <NOME>
  ```

- **Criando uma conexão com o host:** No momento da criação do projeto, é necessário configurar o ip do projeto como `host.docker.internal`. Isso permite que apenas o host possa acessar o container.

- **Conectando um container a uma rede:**

  ```bash
  docker network connect <REDE> <CONTAINER>
  ```

- **Desconectando um container de uma rede:**

  ```bash
  docker network disconnect <REDE> <CONTAINER>
  ```

- **Inspecionando uma rede:**

  ```bash
  docker network inspect <REDE>
  ```

### Tipos de networks:

- **Bridge:** o mais comum e default do Docker, utilizado quando containers precisam se conectar (na maioria das vezes optamos por este driver);

- **host:** permite a conexão entre um container a máquina que está hosteando o Docker;

- **macvlan:** permite a conexão a um container por um MAC address;

- **none:** remove todas conexões de rede de um container;

- **plugins:** permite extensões de terceiros para criar outras redes;

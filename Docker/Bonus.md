## Bônus:

1. Para uma limpeza rápida e eficiente de recursos Docker não utilizados (contêineres parados, imagens sem tags, redes e cache de build), utilize:

   ```bash
   docker system prune -a
   ```

2. Para consultar o funcionamento e as flags de qualquer comando do docker, use:

   ```bash
   docker <COMANDO> --help
   ```

   ou

   ```bash
   docker --help
   ```

3. Autenticação com o Docker Hub, use o comando:

   ```bash
   docker login
   ```

4. Desautenticação com o Docker Hub, use o comando:

   ```bash
   docker logout
   ```

5. Para enviar uma imagem para o Docker Hub, utilize:

   ```bash
   docker push <IMAGEM>
   ```

6. Para limpar os volumes que não estão mais em usado, use o comando:

   ```bash
   docker volume prune
   ```

6. Para limpar as redes que não estão mais em usado, use o comando:

   ```bash
   docker network prune
   ```


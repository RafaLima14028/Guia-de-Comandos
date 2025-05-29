## Dockerfile:

- `FROM`: Define a imagem base a partir da qual sua nova imagem será construída.
- `WORKDIR`: Define o diretório de trabalho.
- `EXPOSE`: Informa ao Docker que o contêiner escutará.
- `COPY`: Copia arquivos ou diretórios do diretório de contexto da construção.
- `ENV`: Define variáveis de ambiente dentro do contêiner.
- `RUN`: Executa qualquer comando em uma nova camada sobre a imagem atual, criando a próxima camada da imagem.
- `CMD`: Fornece padrões para um contêiner em execução ou executa um comando quando o contêiner é iniciado.
- `VOLUME`: Cria um ponto de montagem com o volume especificado, para que os dados possam ser persistidos fora do contêiner.

### Exemplo:

```dockerfile
# Usa a imagem oficial do Node.js como base.
# Escolhemos uma versão LTS (Long Term Support) para estabilidade.
FROM node:20-alpine

# Define uma variável de ambiente. Isso pode ser usado para configurar a aplicação.
ENV NODE_ENV=production
ENV PORT=3000

# Define o diretório de trabalho dentro do contêiner.
# Todos os comandos subsequentes (COPY, RUN, CMD) serão executados a partir daqui.
WORKDIR /app

# Copia os arquivos package.json e package-lock.json (se existir) para o WORKDIR.
# Isso é feito primeiro para aproveitar o cache do Docker.
COPY package*.json .

# Instala as dependências da aplicação, usando a variável de ambiente NODE_ENV.
RUN npm install --omit=dev

# Cria um volume para persistir dados, caso a aplicação precise armazenar algo.
# Neste exemplo, imaginamos que a aplicação possa escrever logs em /app/data.
VOLUME /app/data

# Copia o restante do código da aplicação para o WORKDIR.
COPY . .

# Expõe a porta em que a aplicação Node.js estará escutando, utilizando a variável de ambiente PORT.
EXPOSE $PORT

# Define o comando que será executado quando o contêiner for iniciado.
# Aqui, também podemos usar a variável de ambiente para configurar a inicialização.
CMD ["node", "src/server.js"]
```

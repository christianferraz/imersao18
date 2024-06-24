# Use a imagem base Node.js
FROM node:21-slim

# Defina o diretório de trabalho dentro do contêiner
WORKDIR /home/node/app

# Copie o package.json e o package-lock.json para o diretório de trabalho
COPY --chown=node:node package*.json ./

# Instale as dependências
RUN npm install

# Copie todo o código da aplicação para o diretório de trabalho
COPY --chown=node:node . .

# Construa a aplicação Next.js
RUN npm run build

# Exponha a porta em que a aplicação será executada
EXPOSE 3000

# Defina o usuário para executar o contêiner
USER node

# Comando para iniciar a aplicação Next.js
CMD ["npm", "start"]

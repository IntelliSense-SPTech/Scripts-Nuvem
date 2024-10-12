# Usamos uma imagem oficial do Node.js como base
FROM node:16

# Define o diretório de trabalho dentro do contêiner
WORKDIR /home

# Clona o repositório do GitHub se não existir, caso contrário, faz git pull
RUN if [ ! -d "Front-End" ]; then \
      git clone https://github.com/IntelliSense-SPTech/Front-End; \
    else \
      cd Front-End && git pull; \
    fi

# Muda para o diretório onde está o código da aplicação web dentro do projeto clonado
WORKDIR /home/Front-End

# Instala as dependências do Node.js definidas no package.json
RUN npm install

# Expõe a porta desenvolvimento:3333 ou produção:8080 ou 80 do contêiner, que será usada para acessar a aplicação pela web
EXPOSE 3333

# Define o comando que será executado quando o contêiner iniciar
# Neste caso, ele executa "npm start" para iniciar a aplicação Node.js
CMD ["npm" ,"start"]
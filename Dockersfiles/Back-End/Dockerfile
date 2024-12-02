# Imagem oficial do OpenJDK que contém o apt
FROM openjdk:21-jdk-slim

# Diretório de trabalho dentro do contêiner
WORKDIR /home

# Variáveis de ambiente para o banco de dados (configuradas fora do Dockerfile)
ENV MYSQL_ROOT_PASSWORD=${MYSQL_ROOT_PASSWORD}
ENV DB_USERNAME=${DB_USERNAME}
ENV DB_URL=${DB_URL}
ENV DB_PASSWORD=${DB_PASSWORD}

# Variáveis de ambiente adicionais (configuradas fora do Dockerfile)
ENV AWS_ACCESS_KEY_ID=${AWS_ACCESS_KEY_ID}
ENV AWS_SECRET_ACCESS_KEY=${AWS_SECRET_ACCESS_KEY}
ENV AWS_SESSION_TOKEN=${AWS_SESSION_TOKEN}
ENV S3_BUCKET_NAME=${S3_BUCKET_NAME}
ENV TOKEN_SLACK=${TOKEN_SLACK}

# Instala o Git e o Maven
RUN apt-get update && \
    apt-get install -y git maven && \
    apt-get clean && rm -rf /var/lib/apt/lists/*

# Clona o repositório do GitHub ou faz um git pull se já existir
RUN if [ ! -d "Back-End" ]; then \
        git clone https://github.com/IntelliSense-SPTech/Back-End; \
    else \
        cd Back-End && git pull; \
    fi

# Muda para o diretório onde está o código da aplicação Java dentro do projeto clonado
WORKDIR /home/Back-End

# Compila a aplicação Java usando Maven
RUN mvn clean install

# Expõe a porta usada pela aplicação Java
EXPOSE 8080

# Comando para executar a aplicação Java, esperando o MySQL primeiro
CMD ["java", "-jar", "target/Back-End-IntelliSense-1.0-SNAPSHOT-jar-with-dependencies.jar"]
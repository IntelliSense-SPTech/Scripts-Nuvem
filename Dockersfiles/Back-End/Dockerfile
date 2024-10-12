# Usamos uma imagem oficial do OpenJDK que contém o apt
FROM openjdk:21-jdk-slim

# Define o diretório de trabalho dentro do contêiner
WORKDIR /home

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

# Comando para executar a aplicação Java
CMD ["java", "-jar", "target/Back-End-IntelliSense-1.0-SNAPSHOT-jar-with-dependencies.jar"]

# Imagem oficial do OpenJDK que contém o apt
FROM openjdk:21-jdk-slim

# Diretório de trabalho dentro do contêiner
WORKDIR /home

# Variáveis de ambiente para o banco de dados
ENV MYSQL_ROOT_PASSWORD=123456
ENV DB_USERNAME=intellisense
ENV DB_URL=jdbc:mysql://localhost:3306/intellisense
ENV DB_PASSWORD=123456

# Variáveis de ambiente adicionais
ENV AWS_ACCESS_KEY_ID=ASIAS5ZOKMPOVJ3PXTUV
ENV AWS_SECRET_ACCESS_KEY=EEZlk1N64ggKOvXgfx/2GbAWlKci/CJeX0IkG0rL
ENV AWS_SESSION_TOKEN=IQoJb3JpZ2luX2VjEDEaCXVzLXdlc3QtMiJIMEYCIQDlM2TZEzq9IVGVYIuEPMX+IFmLLiof68JwTFI+17ZNuwIhAMu5N>
ENV S3_BUCKET_NAME=grupointellisense

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

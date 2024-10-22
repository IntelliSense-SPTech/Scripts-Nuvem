# Imagem oficial do MySQL
FROM mysql:8.0

# Variáveis de ambiente para o banco de dados
ENV MYSQL_ROOT_PASSWORD=123456
ENV MYSQL_DATABASE=intellisense
ENV MYSQL_USER=intellisense
ENV MYSQL_PASSWORD=123456

# Script SQL diretamente no Dockerfile
RUN echo "CREATE DATABASE IF NOT EXISTS intellisense;" > /docker-entrypoint-initdb.d/init_db.sql && \
    echo "USE intellisense;" >> /docker-entrypoint-initdb.d/init_db.sql && \
    echo "CREATE TABLE tipo_usuario (id_tipo_usuario INT PRIMARY KEY AUTO_INCREMENT, categoria VARCHAR(40), descric>
    echo "CREATE TABLE localidades (id_localidade INT PRIMARY KEY AUTO_INCREMENT, regiao VARCHAR(40), municipio VAR>
    echo "CREATE TABLE usuarios (id_usuario INT PRIMARY KEY AUTO_INCREMENT, cim CHAR, nome VARCHAR(40), cpf CHAR(14>
    echo "CREATE TABLE crimes (id_crime INT PRIMARY KEY AUTO_INCREMENT, especificacao VARCHAR(255), qtd_casos INT, >
    echo "CREATE TABLE contatos (id_contato INT PRIMARY KEY AUTO_INCREMENT, email VARCHAR(250), mensagem VARCHAR(40>
    echo "CREATE TABLE relatos (id_relato INT PRIMARY KEY AUTO_INCREMENT, fk_usuario INT, descricao VARCHAR(400), d>
    echo "CREATE TABLE avaliacoes (id_avaliacao INT PRIMARY KEY AUTO_INCREMENT, fk_usuario INT, nota INT, mensagem >
    echo "SELECT * FROM crimes;" >> /docker-entrypoint-initdb.d/init_db.sql && \
    echo "TRUNCATE TABLE crimes;" >> /docker-entrypoint-initdb.d/init_db.sql

# Expor a porta padrão do MySQL
EXPOSE 3306
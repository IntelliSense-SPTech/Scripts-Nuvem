# Usar a imagem oficial do MySQL
FROM mysql:8.0

# Variáveis de ambiente para o banco de dados
ENV MYSQL_ROOT_PASSWORD=123456
ENV MYSQL_DATABASE=intellisense
ENV MYSQL_USER=intellisense
ENV MYSQL_PASSWORD=123456

# Script SQL diretamente no Dockerfile
RUN echo "CREATE DATABASE IF NOT EXISTS intellisense;" > /docker-entrypoint-initdb.d/init_db.sql && \
    echo "USE intellisense;" >> /docker-entrypoint-initdb.d/init_db.sql && \
    echo "CREATE TABLE localidades (id_localidade INT PRIMARY KEY AUTO_INCREMENT, regiao VARCHAR(40), municipio VARCHAR(40), populacao FLOAT);" >> /docker-entrypoint-initdb.d/init_db.sql && \
    echo "CREATE TABLE usuarios (id_usuario INT PRIMARY KEY AUTO_INCREMENT, cim CHAR(9), nome VARCHAR(40), tipo_usuario VARCHAR(20), cpf CHAR(14), email VARCHAR(250), senha VARCHAR(40), token CHAR(6), telefone CHAR(11));" >> /docker-entrypoint-initdb.d/init_db.sql && \
    echo "CREATE TABLE crimes (id_crime INT PRIMARY KEY AUTO_INCREMENT, especificacao VARCHAR(255), qtd_casos INT, ano INT, mes INT, fk_localidade INT, FOREIGN KEY (fk_localidade) REFERENCES localidades(id_localidade));" >> /docker-entrypoint-initdb.d/init_db.sql && \
    echo "CREATE TABLE contatos (id_contato INT PRIMARY KEY AUTO_INCREMENT, email VARCHAR(250), mensagem VARCHAR(400));" >> /docker-entrypoint-initdb.d/init_db.sql && \
    echo "CREATE TABLE relatos (id_relato INT PRIMARY KEY AUTO_INCREMENT, fk_usuario INT, descricao VARCHAR(400), data DATE, FOREIGN KEY (fk_usuario) REFERENCES usuarios(id_usuario));" >> /docker-entrypoint-initdb.d/init_db.sql && \
    echo "CREATE TABLE avaliacoes (id_avaliacao INT PRIMARY KEY AUTO_INCREMENT, fk_usuario INT, nota INT, mensagem VARCHAR(400), FOREIGN KEY (fk_usuario) REFERENCES usuarios(id_usuario));" >> /docker-entrypoint-initdb.d/init_db.sql && \
    echo "SELECT * FROM usuarios;" >> /docker-entrypoint-initdb.d/init_db.sql && \
    echo "TRUNCATE TABLE crimes;" >> /docker-entrypoint-initdb.d/init_db.sql

# Expor a porta padrão do MySQL
EXPOSE 3306

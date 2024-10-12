# Usar uma imagem base do MySQL
FROM mysql:latest

# Definir variáveis de ambiente para o banco de dados
ENV MYSQL_DATABASE=meu_banco
ENV MYSQL_USER=meu_usuario
ENV MYSQL_PASSWORD=minha_senha
ENV MYSQL_ROOT_PASSWORD=root_senha

# Instalar Git
RUN apt-get update && \
    apt-get install -y git && \
    apt-get clean

# Clonar o repositório do Git
RUN git clone https://github.com/usuario/repo.git /scripts

# Copiar scripts SQL para o diretório de inicialização do MySQL
COPY /scripts/init_db.sql /docker-entrypoint-initdb.d/

# Expor a porta padrão do MySQL
EXPOSE 3306
